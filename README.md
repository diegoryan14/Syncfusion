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
