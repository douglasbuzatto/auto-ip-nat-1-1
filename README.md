Título: Script para Atualização Automática de Regras NAT 1:1 em Conexões PPPoE

Em redes que utilizam conexão PPPoE, é comum que o endereço IP externo atribuído pelo provedor de internet seja dinâmico, ou seja, mude periodicamente. Quando isso acontece, as regras de NAT 1:1 (Tradução de Endereço de Rede estática) configuradas no roteador precisam ser atualizadas com o novo endereço IP externo para que os serviços e dispositivos internos continuem acessíveis externamente sem interrupções.

Este script tem como objetivo automatizar a atualização das regras de NAT 1:1 sempre que o endereço IP externo da conexão PPPoE mudar. Ao contrário do masquerade NAT, que é recomendado para acesso à internet, o NAT 1:1 permite mapear endereços IP internos específicos para o IP externo, tornando-os acessíveis pela internet.

Benefícios de usar NAT 1:1 ao invés de Masquerade NAT:

1. **Acesso direto a dispositivos/serviços internos**: Com o NAT 1:1, você pode mapear endereços IP internos específicos para o IP externo, permitindo acesso direto a servidores, serviços ou dispositivos em sua rede interna a partir da internet.

2. **Sem necessidade de redirecionamento de portas**: Como cada IP interno é mapeado diretamente para o IP externo, não há necessidade de configurar redirecionamentos de porta, simplificando a configuração.

3. **Suporte a protocolos que não funcionam bem com NAT**: Alguns protocolos ou aplicativos podem ter problemas ao passar pelo masquerade NAT, enquanto funcionam corretamente com o NAT 1:1.

Desvantagens de usar Masquerade NAT:

1. **Acesso direto a dispositivos internos não é possível**: Com o masquerade NAT, você não pode acessar diretamente dispositivos ou serviços em sua rede interna a partir da internet, a menos que configure redirecionamentos de porta manualmente.

2. **Problemas com alguns protocolos**: Certos protocolos ou aplicativos podem enfrentar dificuldades ao passar pelo masquerade NAT, exigindo configurações adicionais.

Funcionalidades do Script:

1. **Detecção Automática de Mudança de IP**: O script monitora a interface PPPoE e obtém o endereço IP externo atualmente atribuído.

2. **Atualização das Regras de NAT 1:1**: Sempre que um novo endereço IP externo é detectado, o script localiza e atualiza as regras de NAT 1:1 existentes no MikroTik, substituindo o endereço IP antigo pelo novo.

3. **Sem Interrupção de Conexões Ativas**: O script atualiza apenas as novas conexões com o novo IP externo, mantendo as conexões existentes inalteradas para evitar interrupções.

4. **Agendamento Automático**: O script é configurado para ser executado periodicamente (por exemplo, a cada minuto) através do agendador do MikroTik, garantindo que as regras de NAT 1:1 estejam sempre atualizadas.

Como Usar:

1. Copie o código do script e crie um novo script no MikroTik através do menu "System > Scripts".
2. Na configuração do script, certifique-se de marcar a opção "Não Exigir Permissões" (don't require permissions).
3. Crie uma nova tarefa no agendador do MikroTik ("System > Scheduler") para executar o script periodicamente (por exemplo, a cada minuto).
4. Verifique se as regras de NAT 1:1 existentes no MikroTik estão corretamente configuradas para a interface PPPoE e os endereços IP internos que você deseja tornar acessíveis externamente.

Com este script implementado, você não precisará mais se preocupar em atualizar manualmente as regras de NAT 1:1 sempre que o endereço IP externo da conexão PPPoE mudar, mantendo seus serviços e dispositivos internos acessíveis externamente de forma confiável e eficiente.
