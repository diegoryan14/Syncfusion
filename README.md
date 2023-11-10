# Syncfusion

/* INPUT */
    :showClearButton='true' /* 'Colocar um Icon de limpar o campo' */

/* GRID */
    clipMode='EllipsisWithTooltip' /* 'Colocar um tooltip nos valores do grid q está cortando' */


/* 'Colocar um Icon na coluna do grid ' */
    <e-column :template="templateOpcoesOcorrencia" headerText='Obs' textAlign='Center' width='80'></e-column>
    templateOpcoes: function () {
        return {
            template: Vue.component('templateOpcoes', {
                template: `
                    <div style='display: flex; justify-content: space-around; align-items: center; gap: 5px;'>
                        <span v-if='image.includes(data.EXTENSAO) || data.EXTENSAO == "pdf" || data.EXTENSAO == "txt"'>
                            <ejs-tooltip
                                position='TopCenter'
                                content="Visualizar">
                                <span
                                    style='width: 10%; cursor: pointer;'
                                    @click='preview(data)'>
                                    <i class="fas fa-eye fa-lg preview"></i>
                                </span>
                            </ejs-tooltip>
                        </span>
                        <ejs-tooltip
                            position='TopCenter'
                            content="Baixar">
                            <span
                                style='width: 10%; cursor: pointer;'
                                @click='baixar(data)'>
                                <i class="fas fa-file-download fa-lg"></i>
                            </span>
                        </ejs-tooltip>
                        <ejs-tooltip
                            position='TopCenter'
                            content="Excluir">
                            <span
                                style='width: 10%; cursor: pointer;'
                                @click='excluir(data)'>
                                <i class="fas fa-trash fa-lg excluir"></i>
                            </span>
                        </ejs-tooltip>
                    </div>
                    `,
                data: function () {
                    return {
                        data: {},
                    };
                },
                methods: {
                }
            })
        }
    },

/* MODAL */

    <ejs-dialog
        isModal='true'
        :buttons="modalButtonsPdf"
        ref="modalPdf"
        :open="(args) => {args.preventFocus = true;} /*tirar o foco do botão primário do modal*/"
        v-bind:visible="false"
        :animationSettings="{ effect: 'Zoom' }"
        :showCloseIcon='false'
        :closeOnEscape='false'
        zIndex="1001"
        target="body"
        style="margin: 10px"
        width="1000px">
        <div class="row">
            <div class="row-input" style="margin: 0px;">
                <div class="col col-md-12">
                    <h4 class="text-center" style="font-weight: bold;">{{input.NOME_PDF}}</h4>
                </div>
                <div id="pdfContainer"></div>
            </div>
        </div>
    </ejs-dialog>

    this.modalButtonsPdf = [{click: this.salvarModal, buttonModel: {cssClass: 'e-outline e-primary', content: '<i class="fas fa-share-square fa-lg"></i>&nbsp&nbspEncaminhar'}},{click: this.fecharModal, buttonModel: {cssClass: 'e-outline e-danger', content: '<i class="fas fa-times-circle"></i>&nbsp&nbspFechar'}}];

    abrirModal(){
        this.$refs.modal_protocol.show();
        this.get_situacao();
        this.get_setor_destino();
    },
    fecharModal(){
        this.$refs.modal_protocol.hide();
        this.limpar_campos_modal();
    },
