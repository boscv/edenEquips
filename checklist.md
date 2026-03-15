# Condições de ativação por automacro

Este documento lista **somente** as **condições** de cada `automacro`, agrupadas por categoria e por seção do arquivo, preservando a ordem de aparecimento no `eventMacros.txt`.


## Glossário


### Configuração
**ConfigKey** - Verdadeiro quando uma ou mais chaves do `config.txt` possuem os valores informados (aceita lista do tipo `chave valor, chave valor...`).  
**ConfigKeyNot** - Verdadeiro quando a chave existe e o valor **não** é o informado.  
**ConfigKeyNotExist** - Verdadeiro quando a chave **não existe** no `config.txt` carregado.  
**ConfigKeyDefined** - Verdadeiro quando a chave existe e está **definida** (não nula/vazia) no `config.txt`.

### Quests
**QuestActive** - Verdadeiro quando a(s) quest(s) de ID informado está(ão) **ativa(s)** no quest log.  
**QuestInactive** - Verdadeiro quando a(s) quest(s) de ID informado **não** está(ão) ativa(s).  
**QuestHuntOngoing** - Verdadeiro quando o objetivo de caça (QuestID + MobID) está **em andamento** (não concluído).  
**QuestHuntCompleted** - Verdadeiro quando o objetivo de caça (QuestID + MobID) está **concluído**.  
**QuestTimeOverdue** - Verdadeiro quando a(s) quest(s) de ID informado está(ão) **overdue/expirada(s)** (fora do prazo).


### Mapa / Entorno
**InMap** - Verdadeiro quando o mapa atual é **um dos** mapas informados (aceita lista).  
**NotInMap** - Verdadeiro quando o mapa atual **não** é o mapa informado.  
**InMapRegex** - Verdadeiro quando o nome do mapa atual **casa com** a expressão regular informada (`/.../`).  
**MobNearDist** - Verdadeiro quando a distância até o monstro mais próximo que casa com o regex informado atende à comparação (ex.: `< 1.5`).  
**ChatRoomNear** - Verdadeiro quando existe um chat room por perto cujo título casa com o regex informado (`/.../`).


### Diálogo / Mensagens
**Console** - Verdadeiro quando a mensagem/linha do console casa com o regex informado (`/.../`).  
**NpcMsg** - Verdadeiro quando a fala/mensagem do NPC casa com o regex informado (`/.../`).


### Status / Recursos
**CurrentHP** - Verdadeiro quando o HP atual atende à comparação informada (suporta valor absoluto e `%`, ex.: `< 60%`).  
**CurrentSP** - Verdadeiro quando o SP atual atende à comparação informada.  
**StatusActiveHandle** - Verdadeiro quando o status/buff identificado pelo *handle* informado está **ativo**.  
**StatusInactiveHandle** - Verdadeiro quando o status/buff identificado pelo *handle* informado está **inativo**.  
**Zeny** - Verdadeiro quando o zeny atual atende à comparação informada.


### Nível / Classe
**BaseLevel** - Verdadeiro quando o Base Level atende ao valor/expressão informada.  
**JobLevel** - Verdadeiro quando o Job Level atende ao valor/intervalo informado (suporta intervalo `x..y`).  
**JobID** - Verdadeiro quando o Job ID atual é **um dos** IDs informados (aceita lista).  
**JobIDNot** - Verdadeiro quando o Job ID atual **não** é nenhum dos IDs informados.


### Inventário / Equipamento
**InInventoryID** - Verdadeiro quando a quantidade do ItemID informado no inventário atende à comparação (ex.: `>= 1`).  
**IsNotEquippedID** - Verdadeiro quando o ItemID informado **não está equipado** (no slot informado, quando aplicável).


### Lógica avançada
**Eval** - Verdadeiro quando a expressão Perl informada em `Eval (...)` retorna **true**.  
**/^(?!).*$/** - Regex. Verdadeiro quando **não** é o valor/expressão informado.  
**$lvl#** - Variável que contém as informações da escolha de Base Level para iniciar as quests.


## Restaurar Configurações


### `resConfig`

- `ConfigKey eden03 4, eden04 4, eden05 4, eden07 4, eden08 4, eden09 4, eden10 4, eden11 4`

**Notas:**
- `exclusive 1`
- `timeout 60`


### `resKafra100`

- `ConfigKey quests100 1`
- `InMapRegex /^(?!moc_para).*$/`

**Notas:**
- `priority 99`
- `disabled 1`


## Salvar na Kafra


### `saveKafra`

- `QuestActive 7138, 7142, 7147, 7214, 7219, 7223, 7229`
- `ConfigKey eden03 0, eden04 0, eden05 0, eden07 0, eden08 0, eden09 0, eden10 0, eden11 0`

**Notas:**
- `timeout 90`
- `exclusive 1`
- `priority 1`


### `saveKafraJuno`

- `Eval ($::config{quests100} > 2)`
- `ConfigKey saveKafraJuno 1`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `saveKafraGeffen`

- `Eval ($::config{quests100} > 2)`
- `ConfigKey saveKafraGeffen 1`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `disabled 1`


### `saveKafraRachel`

- `Eval ($::config{quests100} > 2)`
- `ConfigKey saveKafraRachel 1`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `saveKafraHugel`

- `Eval ($::config{quests100} > 2)`
- `ConfigKey saveKafraHugel 1`

**Notas:**
- `timeout 30`
- `exclusive 1`


## Equips de Aprendiz por Poções


### `goMaquina`

- `JobIDNot 0`
- `ConfigKey trocarPot 1`
- `InInventoryID 5055 >= 1`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `potAprendiz`

- `JobIDNot 0`
- `ConfigKey trocarPot 1`
- `InInventoryID 7059 >= 4`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 2`


## Comprar Asas e Poções


### `checkAsasPots`

- `ConfigKey eden03 1, eden04 1, eden05 1, eden08 1, eden09 1, eden10 1, eden11 1`
- `CurrentHP > 1`

**Notas:**
- `timeout 60`
- `exclusive 1`


## Equipamentos


### `equips100`

- `InInventoryID 25223 > 19`
- `ConfigKey equips100 1`
- `ConfigKeyNot equips100 ok`

**Notas:**
- `timeout 120`
- `exclusive 1`


### `equips115`

- `InInventoryID 25223 > 59`
- `BaseLevel > 114`
- `ConfigKey equips115 1`
- `ConfigKeyNot equips115 ok`

**Notas:**
- `timeout 120`
- `exclusive 1`


### `equips130`

- `InInventoryID 25223 > 79`
- `BaseLevel > 129`
- `ConfigKey equips130 1`
- `ConfigKeyNot equips130 ok`

**Notas:**
- `timeout 120`
- `exclusive 1`


### `equips145`

- `InInventoryID 25223 > 109`
- `BaseLevel > 144`
- `ConfigKey equips145 1`
- `ConfigKeyNot equips145 ok`

**Notas:**
- `timeout 120`
- `exclusive 1`


### `equips160`

- `InInventoryID 25223 > 149`
- `BaseLevel > 159`
- `ConfigKey equips160 1`
- `ConfigKeyNot equips160 ok`

**Notas:**
- `timeout 120`
- `exclusive 1`


### `boina100`

- `InInventoryID 25223 > 69`
- `ConfigKey boinaI 1`
- `ConfigKeyNot boinaI ok`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `boina160`

- `InInventoryID 25223 > 599`
- `ConfigKey boinaII 1`
- `ConfigKeyNot boinaII ok`

**Notas:**
- `timeout 30`
- `exclusive 1`


## Reset de Quest


### `resetQuest`

- `ConfigKey eden03 2, eden04 2,  eden05 2, eden07 2,  eden08 2, eden09 2, eden10 2, eden11 2`
- `CurrentHP 1`

**Notas:**
- `overrideAI 1`
- `timeout 300`
- `exclusive 1`


## Equipar Éden Auto


### `equipar07`

- `BaseLevel == 7..25`
- `InInventoryID 15009 > 0`
- `IsNotEquippedID armor 2456`
- `IsNotEquippedID armor 2560`
- `IsNotEquippedID armor 5583`
- `IsNotEquippedID armor 15009`

**Notas:**
- `exclusive 1`
- `priority 1`
- `run-once 1`


### `equipar26`

- `BaseLevel == 26..39`
- `InInventoryID 15010 > 0`
- `IsNotEquippedID rightHand 13050`
- `IsNotEquippedID rightHand 1192`
- `IsNotEquippedID rightHand 1650`
- `IsNotEquippedID rightHand 1747`
- `IsNotEquippedID rightHand 13112`
- `IsNotEquippedID rightHand 13423`
- `IsNotEquippedID rightHand 16004`
- `IsNotEquippedID rightHand 1699`
- `IsNotEquippedID armor 2457`
- `IsNotEquippedID armor 2560`
- `IsNotEquippedID armor 5583`
- `IsNotEquippedID armor 15010`

**Notas:**
- `exclusive 1`
- `priority 1`
- `run-once 1`


### `equipar40`

- `BaseLevel == 40..59`
- `InInventoryID 15011 > 0`
- `IsNotEquippedID rightHand 13051`
- `IsNotEquippedID rightHand 1193`
- `IsNotEquippedID rightHand 1651`
- `IsNotEquippedID rightHand 1748`
- `IsNotEquippedID rightHand 13113`
- `IsNotEquippedID rightHand 13424`
- `IsNotEquippedID rightHand 16005`
- `IsNotEquippedID rightHand 26100`
- `IsNotEquippedID armor 2458`
- `IsNotEquippedID armor 2560`
- `IsNotEquippedID armor 5583`
- `IsNotEquippedID armor 15011`

**Notas:**
- `exclusive 1`
- `priority 1`
- `run-once 1`


### `equipar60`

- `BaseLevel == 60..99`
- `InInventoryID 15031 > 0`
- `IsNotEquippedID rightHand 1197`
- `IsNotEquippedID rightHand 13434`
- `IsNotEquippedID rightHand 13066`
- `IsNotEquippedID rightHand 1289`
- `IsNotEquippedID rightHand 1391`
- `IsNotEquippedID rightHand 1434`
- `IsNotEquippedID rightHand 1658`
- `IsNotEquippedID rightHand 16014`
- `IsNotEquippedID rightHand 18106`
- `IsNotEquippedID rightHand 1583`
- `IsNotEquippedID rightHand 1931`
- `IsNotEquippedID rightHand 1986`
- `IsNotEquippedID rightHand 13114`
- `IsNotEquippedID rightHand 1831`
- `IsNotEquippedID rightHand 13310`
- `IsNotEquippedID rightHand 26101`
- `IsNotEquippedID armor 2473`
- `IsNotEquippedID armor 2571`
- `IsNotEquippedID armor 15031`

**Notas:**
- `exclusive 1`
- `priority 1`
- `run-once 1`


## Quest Éden (7) - Acadêmia Criatura


### `eden00`

- `JobIDNot 0`
- `InInventoryID 22508 == 0`

**Notas:**
- `overrideAI 0`
- `timeout 60`
- `exclusive 1`
- `delay 30`


## Quest Éden (26-32) - Caverna de Payon


### `eden03`

- `BaseLevel == 26..32`
- `BaseLevel == $lvl03`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lvlQuest03 off`
- `ConfigKeyNotExist eden03`
- `InInventoryID 15010 == 0`

**Notas:**
- `timeout 300`
- `exclusive 1`


### `goCoral`

- `QuestActive 7138`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden03 2`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goEsqueleto`

- `QuestHuntOngoing 7139 1076`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden03 2`
- `CurrentHP >= 90%`
- `InMapRegex /^(?!pay_dun00).*$/`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `esqueletoOk`

- `QuestHuntCompleted 7139 1076`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `goPoporing`

- `QuestHuntOngoing 7140 1031`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden03 2`
- `CurrentHP >= 90%`
- `InMapRegex /^(?!pay_dun00).*$/`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `poporingOk`

- `QuestHuntCompleted 7140 1031`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `eden03Ok`

- `QuestActive 7141`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `equips03`

- `ConfigKey eden03 3`

**Notas:**
- `exclusive 1`
- `timeout 30`


## Quest Éden (33-39) - Formigueiro Infernal


### `eden04`

- `BaseLevel == 33..39`
- `BaseLevel == $lvl04`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lvlQuest04 off`
- `ConfigKeyNotExist eden04`
- `InInventoryID 15010 == 0`

**Notas:**
- `timeout 300`
- `exclusive 1`


### `goClod`

- `QuestActive 7142`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden04 2`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goPierre`

- `QuestHuntOngoing 7143 1160`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden04 2`
- `CurrentHP >= 90%`
- `InMapRegex /^(?!anthell01).*$/`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `pierreOk`

- `QuestHuntCompleted 7143 1160`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden04 2`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `goAndre`

- `QuestHuntOngoing 7144 1095`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden04 2`
- `CurrentHP >= 90%`
- `InMapRegex /^(?!anthell01).*$/`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `andreOk`

- `QuestHuntCompleted 7144 1095`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden04 2`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `goVitata`

- `QuestHuntOngoing 7145 1176`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden04 2`
- `CurrentHP >= 90%`
- `InMapRegex /^(?!anthell01).*$/`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `vitataOk`

- `QuestHuntCompleted 7145 1176`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden04 2`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `eden04Ok`

- `QuestActive 7146`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `equips04`

- `ConfigKey eden04 3`

**Notas:**
- `exclusive 1`
- `timeout 30`


## Quest Éden (40-49) - Vila dos Orcs


### `eden05`

- `BaseLevel == 40..49`
- `BaseLevel == $lvl05`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lvlQuest05 off`
- `ConfigKeyNotExist eden05`
- `InInventoryID 15011 == 0`

**Notas:**
- `timeout 300`
- `exclusive 1`


### `goAbsalom`

- `QuestActive 7147`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden05 2`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goFilhote`

- `QuestHuntOngoing 7148 1686`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden05 2`
- `CurrentHP >= 90%`
- `InMapRegex /^(?!gef_fild10$|gef_f10_[abcd]$).*/`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `filhoteOk`

- `QuestHuntCompleted 7148 1686`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden05 2`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `goGuerreiro`

- `QuestHuntOngoing 7149 1023`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden05 2`
- `CurrentHP >= 90%`
- `InMapRegex /^(?!gef_fild10|gef_f10_[abcd]$).*$/`

**Notas:**
- `timeout 15`


### `guerreiroOk`

- `QuestHuntCompleted 7149 1023`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden05 2`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `goSenhora`

- `QuestHuntOngoing 7150 1273`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden05 2`
- `CurrentHP >= 90%`
- `InMapRegex /^(?!gef_fild10|gef_f10_[abcd]$).*$/`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `senhoraOK`

- `QuestHuntCompleted 7150 1273`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden05 2`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `eden05Ok`

- `QuestActive 7151`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `equips05`

- `ConfigKey eden05 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


## Quest Éden (75-99) - Ilha Byalan


### `eden07`

- `BaseLevel == 75..99`
- `BaseLevel == $lvl07`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lvlQuest07 off`
- `ConfigKeyNotExist eden07`
- `InInventoryID 15011 == 0`

**Notas:**
- `timeout 300`
- `exclusive 1`


### `goCallandiva`

- `QuestActive 7156`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden07 2`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goTritao`

- `QuestHuntOngoing 7157 1264`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden07 2`
- `CurrentHP >= 90%`
- `InMapRegex /^(?!iz_dun04).*$/`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `tritaoOk`

- `QuestHuntCompleted 7157 1264`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden07 2`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `goStrouf`

- `QuestHuntOngoing 7158 1065`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden07 2`
- `CurrentHP >= 90%`
- `InMapRegex /^(?!iz_dun04).*$/`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `stroufOk`

- `QuestHuntCompleted 7158 1065`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden07 2`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `eden07Ok`

- `QuestActive 7159`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `equips07`

- `ConfigKey eden07 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


## Quest Éden (60-69) - Comodo


### `eden08`

- `BaseLevel == 60..69`
- `BaseLevel == $lvl08`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lvlQuest08 off`
- `ConfigKeyNotExist eden08`
- `InInventoryID 15031 == 0`
- `JobIDNot 1`
- `JobIDNot 2`
- `JobIDNot 3`
- `JobIDNot 4`
- `JobIDNot 5`
- `JobIDNot 6`
- `JobIDNot 4046`

**Notas:**
- `timeout 300`
- `exclusive 1`


### `goRomeo`

- `QuestActive 7214`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden08 2`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goGolem01`

- `QuestHuntOngoing 7215 1278`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden08 2`
- `CurrentHP >= 90%`
- `InMapRegex /^(?!beach_dun2).*$/`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `golem01Ok`

- `QuestHuntCompleted 7215 1278`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `goGolem02`

- `QuestHuntOngoing 7216 1278`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden08 2`
- `CurrentHP >= 90%`
- `InMapRegex /^(?!beach_dun2).*$/`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `golem02Ok`

- `QuestHuntCompleted 7216 1278`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `goFolhaOmbreira`

- `QuestActive 7217`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden08 2`
- `CurrentHP >= 90%`
- `InMapRegex /^(?!um_fild01|um_fild02).*$/`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `stealFolha`

- `QuestActive 7217`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `JobID 6, 12, 17`
- `ConfigKey eden08 2`
- `CurrentSP >= 10`
- `InInventoryID 7100 < 7`
- `MobNearDist /(Dríade)/ < 1.5`

**Notas:**
- `timeout 8`


### `stealOmbreira`

- `QuestActive 7217`
- `JobID 6, 12, 17`
- `ConfigKey eden08 2`
- `CurrentSP >= 10`
- `InInventoryID 7196 < 5`
- `MobNearDist /(Guerreiro)/ < 1.5`

**Notas:**
- `timeout 8`


### `faltaOmbreira`

- `QuestActive 7217`
- `NotInMap um_fild02`
- `ConfigKey eden08 2`
- `InInventoryID 7100 >= 7`
- `InInventoryID 7196 < 5`

**Notas:**
- `priority 1`
- `timeout 15`
- `exclusive 1`


### `folhaOk`

- `QuestActive 7217`
- `InInventoryID 7100 >= 7`

**Notas:**
- `priority 1`
- `timeout	600`
- `exclusive 1`


### `ombreirasOk`

- `QuestActive 7217`
- `InInventoryID 7196 >= 5`

**Notas:**
- `priority 1`
- `timeout	600`
- `exclusive 1`


### `folhaOmbreiraOk`

- `QuestActive 7217`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InInventoryID 7100 >= 7`
- `InInventoryID 7196 >= 5`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `eden08Ok`

- `QuestActive 7218`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `equips08`

- `ConfigKey eden08 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


## Quest Éden (70-79) - Glastheim


### `eden09`

- `BaseLevel == 70..79`
- `BaseLevel == $lvl09`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lvlQuest09 off`
- `ConfigKeyNotExist eden09`

**Notas:**
- `timeout 300`
- `exclusive 1`


### `goJohan`

- `QuestActive 7219`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden09 2`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goPenada`

- `QuestHuntOngoing 7220 1192`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden09 2`
- `CurrentHP >= 90%`
- `InMapRegex /^(?!gl_church).*$/`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `penadaOk`

- `QuestHuntCompleted 7220 1192`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden09 2`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `goMaligno`

- `QuestHuntOngoing 7221 1117`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden09 2`
- `CurrentHP >= 90%`
- `InMapRegex /^(?!gl_church).*$/`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `malignoOk`

- `QuestHuntCompleted 7221 1117`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden09 2`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `eden09Ok`

- `QuestActive 7222`

**Notas:**
- `timeout 300`
- `exclusive 1`


### `equips09`

- `ConfigKey eden09 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


## Quest Éden (80-89) - Einbroch


### `eden10`

- `BaseLevel == 80..89`
- `BaseLevel == $lvl10`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lvlQuest10 off`
- `ConfigKeyNotExist eden10`

**Notas:**
- `timeout 300`
- `exclusive 1`


### `goGirhen`

- `QuestActive 7223`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden10 2`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goPorcelios`

- `QuestHuntOngoing 7224 1619`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden10 2`
- `CurrentHP >= 90%`
- `InMapRegex /^(?!ein_fild08).*$/`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `porceliosOk`

- `QuestHuntCompleted 7224 1619`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden10 2`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `goNuvemUrsinho`

- `QuestHuntOngoing 7226 1621, 7227 1622`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden10 2`
- `CurrentHP >= 90%`
- `InMapRegex /^(?!ein_fild04).*$/`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `nuvemOK`

- `QuestHuntCompleted 7226 1621`

**Notas:**
- `priority 1`
- `timeout 600`
- `exclusive 1`


### `ursinhoOK`

- `QuestHuntCompleted 7227 1622`

**Notas:**
- `priority 1`
- `timeout 600`
- `exclusive 1`


### `nuvemUrsinhoOk`

- `QuestHuntCompleted 7226 1621`
- `QuestHuntCompleted 7227 1622`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden10 2`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `eden10Ok`

- `QuestActive 7228`

**Notas:**
- `timeout 60`
- `exclusive 1`


### `equips10`

- `ConfigKey eden10 3`

**Notas:**
- `exclusive 1`
- `timeout 30`


## Quest Éden (90-99) - Caverna de Gelo


### `eden11`

- `BaseLevel == 90..99`
- `BaseLevel == $lvl11`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lvlQuest11 off`
- `ConfigKeyNotExist eden11`

**Notas:**
- `timeout 300`
- `exclusive 1`


### `leite`

- `QuestActive 7229, 7230, 7231`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InInventoryID 519 < 1`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 0`


### `molho`

- `QuestActive 7229, 7230, 7231`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden11 2`
- `InInventoryID 519 >= 1`
- `InInventoryID 7453 < 1`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 0`


### `goNeomi`

- `QuestActive 7229`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden11 2`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `goSiroma`

- `QuestHuntOngoing 7230 1776`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden11 2`
- `CurrentHP >= 90%`
- `InMapRegex /^(?!ice_dun01).*$/`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `siromaOK`

- `QuestHuntCompleted 7230 1776`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden11 2`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `goSiroma2`

- `QuestActive 7231`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey eden11 2`
- `CurrentHP >= 90%`
- `InMapRegex /^(?!ice_dun01).*$/`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `stealGelo`

- `QuestActive 7230, 7231`
- `JobID 6, 12, 17`
- `ConfigKey eden11 2`
- `CurrentSP >= 10`
- `InInventoryID 7066 < 30`
- `MobNearDist /(Siroma)/ < 1.5`

**Notas:**
- `timeout 8`


### `siroma2OK`

- `QuestHuntCompleted 7231 1776`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InInventoryID 7066 >= 30`
- `ConfigKey eden11 2`

**Notas:**
- `timeout 15`
- `exclusive 1`


### `eden11Ok`

- `QuestActive 7232`

**Notas:**
- `timeout 60`
- `exclusive 1`


### `equips11`

- `ConfigKey eden11 3`

**Notas:**
- `exclusive 1`
- `timeout 30`


## Novo Mundo


### `novoMundo`

- `BaseLevel >= 80`
- `ConfigKey novoMundo 1`
- `Zeny > 55000`

**Notas:**
- `timeout 180`
- `exclusive 1`


### `mid_camp`

- `ConfigKey novoMundo 2`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`

**Notas:**
- `timeout 180`
- `exclusive 1`


## Caverna De Magma (100)


### `ativarMagma100`

- `BaseLevel > 99`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey quests100 1`
- `ConfigKey magma100_0 1, magma100_1 1, magma100_2 1`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `dailyMagma100`

- `QuestTimeOverdue 21630, 21633, 21636`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey quests100 1`
- `ConfigKey magma100_0 2, magma100_1 2, magma100_2 2`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `mag_dun01`

- `QuestActive 21637`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKey magma100_2 3`
- `InMapRegex /^(?!mag_dun01).*$/`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `pome_Ok`

- `QuestActive 21637`
- `InInventoryID 7096 > 9`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `mag_dun02`

- `QuestActive 21631, 21534`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKeyNot magma100_2 3`
- `ConfigKey magma100_0 3, magma100_1 3`
- `InMapRegex /^(?!mag_dun02).*$/`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `pesadelo_Ok`

- `QuestHuntCompleted 21631 1379`
- `ConfigKey magma100_0 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `exterminador_Ok`

- `QuestHuntCompleted 21634 1384`
- `ConfigKey magma100_1 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `deleterio_Ok`

- `QuestHuntCompleted 21634 1385`
- `ConfigKey magma100_1 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `magma_Ok`

- `ConfigKey magma100_0 4, magma100_1 4, magma100_2 4`
- `ConfigKey quests100 2`

**Notas:**
- `timeout 30`


## Glastheim (100-110)


### `ativarGl100_110`

- `BaseLevel > 99`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey quests100 1`
- `ConfigKey gl100_0 1, gl100_1 1, gl100_2 1, gl100_3 1, gl100_4 1, gl110_5 1, gl110_6 1, gl110_7 1, gl110_8 1`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 2`


### `dailyGl100_110`

- `QuestTimeOverdue 21684, 21687, 21690, 21693, 21696, 21699, 21702, 21705, 21708`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey quests100 1`
- `ConfigKey gl100_0 2, gl100_1 2, gl100_2 2, gl100_3 2, gl100_4 2, gl110_5 2, gl110_6 2, gl110_7 2, gl110_8 2`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 2`


### `gl_dun01`

- `QuestActive 21688, 21691, 21694`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKey gl100_1 3, gl100_2 3, gl100_3 3`
- `InMapRegex /^(?!gl_dun01).*$/`

**Notas:**
- `timeout 30`
- `priority 2`


### `arclouse_Ok`

- `QuestHuntCompleted 21688 1194`
- `ConfigKey gl100_1 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `anolian_Ok`

- `QuestHuntCompleted 21691 1206`
- `ConfigKey gl100_2 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `sting_Ok`

- `QuestHuntCompleted 21694 1207`
- `ConfigKey gl100_3 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `gl_dun02`

- `QuestActive 21697`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKeyNot gl100_1 3, gl100_2 3, gl100_3 3`
- `ConfigKey gl100_4 3`
- `InMapRegex /^(?!gl_dun02).*$/`

**Notas:**
- `timeout 30`
- `priority 2`


### `majoruros_Ok`

- `QuestHuntCompleted 21697 1310`
- `ConfigKey gl100_4 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `gl_cas01`

- `QuestActive 21685`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKeyNot gl100_1 3, gl100_2 3, gl100_3 3, gl100_4 3`
- `ConfigKey gl100_0 3`
- `InMapRegex /^(?!gl_cas01).*$/`

**Notas:**
- `timeout 30`
- `priority 2`


### `carat_Ok`

- `QuestHuntCompleted 21685 1267`
- `ConfigKey gl100_0 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `gl_cas02`

- `QuestActive 21706`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKeyNot gl100_0 3, gl100_1 3, gl100_2 3, gl100_3 3, gl100_4 3`
- `ConfigKey gl110_7 3`
- `InMapRegex /^(?!gl_cas02).*$/`

**Notas:**
- `timeout 30`
- `priority 2`


### `andarilho_Ok`

- `QuestHuntCompleted 21706 1208`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `gl_knt01`

- `QuestActive 21700, 21709`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKeyNot gl100_0 3, gl100_1 3, gl100_2 3, gl100_3 3, gl100_4 3, gl110_7 3`
- `ConfigKey gl110_5 3,  gl110_8 3`
- `InMapRegex /^(?!gl_knt01).*$/`

**Notas:**
- `timeout 30`
- `priority 2`


### `raydric_Ok`

- `QuestHuntCompleted 21700 1132`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `abismo_Ok`

- `QuestHuntCompleted 21709 1219`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `gl_knt02`

- `QuestActive 21703`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKeyNot gl100_0 3, gl100_1 3, gl100_2 3, gl100_3 3, gl100_4 3, gl110_5 3, gl110_7 3, gl110_8 3`
- `ConfigKey gl110_6 3`
- `InMapRegex /^(?!gl_knt02).*$/`

**Notas:**
- `timeout 30`
- `priority 2`


### `khalitzburg_Ok`

- `QuestHuntCompleted 21703 1163`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `gl_Ok`

- `ConfigKey gl100_0 4, gl100_1 4, gl100_2 4, gl100_3 4, gl100_4 4, gl110_5 4, gl110_6 4, gl110_7 4, gl110_8 4`
- `ConfigKey quests100 2`

**Notas:**
- `timeout 30`
- `exclusive 1`


## Ash Vacuum (100-110)


### `ativarAsh100_110`

- `BaseLevel > 99`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey quests100 1`
- `ConfigKey ash100_0 1, ash100_1 1, ash100_2 1, ash110_3 1, ash110_4 1, ash110_5 1, ash110_6 1, ash110_7 1, ash110_7 1`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 3`


### `dailyAsh100_110`

- `QuestTimeOverdue 21714, 21717, 21720, 21723, 21726, 21729, 21732, 21735, 21738`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey quests100 1`
- `ConfigKey ash100_0 2, ash100_1 2, ash100_2 2, ash110_3 2, ash110_4 2, ash110_5 2, ash110_6 2, ash110_7 2, ash110_8 2`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 3`


### `spl_fild02`

- `QuestActive 21715`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKey ash100_0 3`
- `InMapRegex /^(?!spl_fild02).*$/`

**Notas:**
- `timeout 30`
- `priority 3`


### `pinguicula_Ok`

- `QuestHuntCompleted 21715 1995`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `spl_fild03`

- `QuestActive 21718, 21721`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKey ash100_1 3, ash100_2 3`
- `ConfigKeyNot ash100_0 3`
- `InMapRegex /^(?!spl_fild03).*$/`

**Notas:**
- `timeout 30`
- `priority 3`


### `vespaVagalume_Ok`

- `QuestHuntCompleted 21718 1994`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `leaoDeVinhas_Ok`

- `QuestHuntCompleted 21721 1991`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `spl_fild01`

- `QuestActive 21724, 21730, 21733`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKey ash110_3 3, ash110_5 3, ash110_6 3, ash110_8 3`
- `ConfigKeyNot ash100_0 3, ash100_1 3, ash100_2 3`
- `InMapRegex /^(?!spl_fild01).*$/`

**Notas:**
- `timeout 30`
- `priority 3`


### `pinguiculaSombria_Ok`

- `QuestHuntCompleted 21724 2015`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `naga_Ok`

- `QuestHuntCompleted 21730 1993`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `cornus_Ok`

- `QuestHuntCompleted 21733 1992`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `chifre_Ok`

- `QuestActive 21739`
- `ConfigKey ash110_8 3`
- `InInventoryID 6023 > 19`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `man_fild01`

- `QuestActive 21727, 21736`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKey ash110_4 3, ash110_7 3`
- `ConfigKeyNot ash100_0 3, ash100_1 3, ash100_2 3, ash110_3 3, ash110_5 3, ash110_6 3, ash110_8 3`
- `InMapRegex /^(?!man_fild01).*$/`

**Notas:**
- `timeout 30`
- `priority 3`


### `nepenthes_Ok`

- `QuestHuntCompleted 21727 1988`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `larvaDeCentopeia_Ok`

- `QuestHuntCompleted 21736 1999`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `ash_Ok`

- `ConfigKey ash100_0 4, ash100_1 4, ash100_2 4, ash110_3 4, ash110_4 4, ash110_5 4, ash110_6 4, ash110_7 4, ash110_8 4`
- `ConfigKey quests100 2`

**Notas:**
- `timeout 30`
- `exclusive 1`


## Arunafeltz (100)


### `ativarAruna100`

- `BaseLevel > 99`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey quests100 1`
- `ConfigKey aruna100_0 1, aruna100_1 1, aruna100_2 1, aruna100_3 1, aruna100_4 1, aruna100_5 1, aruna100_6 1, aruna100_7 1, aruna100_8 1`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 4`


### `dailyAruna100`

- `QuestTimeOverdue 21376, 21378, 21386, 21380, 21382, 21384, 21388, 21390, 21392`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey quests100 1`
- `ConfigKey aruna100_0 2, aruna100_1 2, aruna100_2 2, aruna100_3 2, aruna100_4 2, aruna100_5 2, aruna100_6 2, aruna100_7 2, aruna100_8 2`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 4`


### `ve_fild03`

- `QuestActive 21383`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKey aruna100_5 3`
- `InMapRegex /^(?!ve_fild03).*$/`

**Notas:**
- `timeout 30`
- `priority 4`


### `magmaring_Ok`

- `QuestHuntCompleted 21383 1836`
- `ConfigKey aruna100_5 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `ve_fild04`

- `QuestActive 21381`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKeyNot aruna100_5 3`
- `ConfigKey aruna100_4 3`
- `InMapRegex /^(?!ve_fild04).*$/`

**Notas:**
- `timeout 30`
- `priority 4`


### `drosera_Ok`

- `QuestHuntCompleted 21381 1780`
- `ConfigKey aruna100_4 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `miscipular_Ok`

- `QuestHuntCompleted 21381 1781`
- `ConfigKey aruna100_4 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `ra_fild04`

- `QuestActive 21377`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKeyNot aruna100_4 3, aruna100_5 3`
- `ConfigKey aruna100_1 3`
- `InMapRegex /^(?!ra_fild04).*$/`

**Notas:**
- `timeout 30`
- `priority 4`


### `ventoDaColina_Ok`

- `QuestHuntCompleted 21377 1680`
- `ConfigKey aruna100_1 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `ra_fild05`

- `QuestActive 21375`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKeyNot aruna100_1 3, aruna100_4 3, aruna100_5 3`
- `ConfigKey aruna100_0 3, aruna100_3 3`
- `InMapRegex /^(?!ra_fild05).*$/`

**Notas:**
- `timeout 30`
- `priority 4`


### `koboldMachado_Ok`

- `QuestHuntCompleted 21375 1133`
- `ConfigKey aruna100_0 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `koboldMartelo_Ok`

- `QuestHuntCompleted 21375 1134`
- `ConfigKey aruna100_0 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `koboldMaca_Ok`

- `QuestHuntCompleted 21375 1135`
- `ConfigKey aruna100_0 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `cabeloAzul_Ok`

- `QuestActive 21379`
- `ConfigKey aruna100_3 3`
- `InInventoryID 1034 > 19`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `ra_fild01`

- `QuestActive 21385`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKeyNot aruna100_0 3, aruna100_1 3, aruna100_3 3, aruna100_4 3, aruna100_5 3`
- `ConfigKey  aruna100_2 3`
- `InMapRegex /^(?!ra_fild01).*$/`

**Notas:**
- `timeout 30`
- `priority 4`


### `loboDeserto_Ok`

- `QuestHuntCompleted 21385 1106`
- `ConfigKey aruna100_2 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `ice_dun03`

- `QuestActive 21391`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKeyNot aruna100_0 3, aruna100_1 3, aruna100_2 3, aruna100_3 3, aruna100_4 3, aruna100_5 3`
- `ConfigKey aruna100_8 3`
- `InMapRegex /^(?!ice_dun03).*$/`

**Notas:**
- `timeout 30`
- `priority 4`


### `titaDeGelo_Ok`

- `QuestHuntCompleted 21391 1777`
- `ConfigKey aruna100_8 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `gazeti_Ok`

- `QuestHuntCompleted 21391 1778`
- `ConfigKey aruna100_8 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `ice_dun02`

- `QuestActive 21387, 21389`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKeyNot aruna100_0 3, aruna100_1 3, aruna100_2 3, aruna100_3 3, aruna100_4 3, aruna100_5 3, aruna100_8 3`
- `ConfigKey aruna100_6 3, aruna100_7 3`
- `InMapRegex /^(?!ice_dun02).*$/`

**Notas:**
- `timeout 30`
- `priority 4`


### `coracaoGlacial_Ok`

- `QuestActive 21387`
- `ConfigKey aruna100_6 3`
- `InInventoryID 7561 > 19`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `yeti_Ok`

- `QuestHuntCompleted 21389 1775`
- `ConfigKey aruna100_7 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `aruna_Ok`

- `ConfigKey aruna100_0 4, aruna100_1 4, aruna100_2 4, aruna100_3 4, aruna100_4 4, aruna100_5 4, aruna100_6 4, aruna100_7 4, aruna100_8 4`
- `ConfigKey quests100 2`

**Notas:**
- `timeout 30`
- `exclusive 1`


## Torre De Thanatos (110)


### `ativarThana110`

- `BaseLevel > 109`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey quests100 1`
- `ConfigKey thana110_0 1, thana110_1 1, thana110_2 1, thana110_3 1, thana110_4 1, thana110_5 1`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 5`


### `dailyThana110`

- `QuestTimeOverdue 21652, 21655, 21658, 21661, 21664, 21667`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey quests100 1`
- `ConfigKey thana110_0 2, thana110_1 2, thana110_2 2, thana110_3 2, thana110_4 2, thana110_5 2`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 5`


### `tha_t02`

- `QuestActive 21653`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKey thana110_0 3`
- `InMapRegex /^(?!tha_t02).*$/`

**Notas:**
- `timeout 30`
- `priority 5`


### `mimicoAntigo_Ok`

- `QuestHuntCompleted 21653 1699`
- `ConfigKey thana110_0 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `tha_t03`

- `QuestActive 21656, 21662`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKeyNot thana110_0 3`
- `ConfigKey thana110_1 3, thana110_3 3`
- `InMapRegex /^(?!tha_t03).*$/`

**Notas:**
- `timeout 30`
- `priority 5`


### `palavraMorta_Ok`

- `QuestHuntCompleted 21656 1698`
- `ConfigKey thana110_1 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `paginaSangrenta_Ok`

- `QuestActive 21662`
- `ConfigKey thana110_3 3`
- `InInventoryID 7449 > 9`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `tha_t06`

- `QuestActive 21659, 21665, 21668`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKeyNot thana110_0 3, thana110_1 3, thana110_3 3`
- `ConfigKey  thana110_2 3, thana110_4 3, thana110_5 3`
- `InMapRegex /^(?!tha_t06).*$/`

**Notas:**
- `timeout 30`
- `priority 5`


### `baraoCoruja_Ok`

- `QuestHuntCompleted 21659 1295`
- `ConfigKey thana110_2 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `pergaminho_Ok`

- `QuestActive 21665`
- `ConfigKey thana110_4 3`
- `InInventoryID 7099 > 19`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `farrapos_Ok`

- `QuestActive 21668`
- `ConfigKey thana110_5 3`
- `InInventoryID 7071 > 19`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `thana_Ok`

- `ConfigKey thana110_0 4, thana110_1 4, thana110_2 4, thana110_3 4, thana110_4 4, thana110_5 4`
- `ConfigKey quests100 2`

**Notas:**
- `timeout 30`
- `exclusive 1`


## Juperos (110)


### `ativarJupe110`

- `BaseLevel > 109`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey quests100 1`
- `ConfigKey jupe110_0 1, jupe110_1 1, jupe110_2 1, jupe110_3 1, jupe110_4 1`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 6`


### `dailyJupe110`

- `QuestTimeOverdue 21354, 21352, 21356, 21358`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey quests100 1`
- `ConfigKey jupe110_0 2, jupe110_1 2, jupe110_2 2, jupe110_3 2, jupe110_4 2`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 6`


### `juperos_01`

- `QuestActive 21353, 21351, 32355, 21357`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKey jupe110_0 3, jupe110_1 3, jupe110_2 3, jupe110_3 3`
- `InMapRegex /^(?!juperos_01).*$/`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 6`


### `venatuLaranja_Ok`

- `QuestHuntCompleted 21353 1678`
- `ConfigKey jupe110_0 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `venatuAzul_Ok`

- `QuestHuntCompleted 21353 1679`
- `ConfigKey jupe110_0 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `venatuRoxo_Ok`

- `QuestHuntCompleted 21351 1676`
- `ConfigKey jupe110_1 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `venatuVerde_Ok`

- `QuestHuntCompleted 21351 1677`
- `ConfigKey jupe110_1 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `dimikVerde_Ok`

- `QuestHuntCompleted 21355 1670`
- `ConfigKey jupe110_2 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `dimikAzul_Ok`

- `QuestHuntCompleted 21355 1671`
- `ConfigKey jupe110_2 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `dimikVermelho_Ok`

- `QuestHuntCompleted 21357 1672`
- `ConfigKey jupe110_3 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `dimikLaranja_Ok`

- `QuestHuntCompleted 21357 1673`
- `ConfigKey jupe110_3 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `jupe_Ok`

- `ConfigKey jupe110_0 4, jupe110_1 4, jupe110_2 4, jupe110_3 4`
- `ConfigKey quests100 2`

**Notas:**
- `timeout 30`
- `exclusive 1`


## Templo De Odin (120)


### `ativarOdin120`

- `BaseLevel > 119`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey quests100 1`
- `ConfigKey odin120_0 1, odin120_1 1, odin120_2 1`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 7`


### `dailyOdin120`

- `QuestTimeOverdue 21583, 21586, 21589`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey quests100 1`
- `ConfigKey odin120_0 2, odin120_1 2, odin120_2 2`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 7`


### `odin_tem02`

- `QuestActive 21584,`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKey odin120_0 3, odin120_1 3`
- `InMapRegex /^(?!odin_tem02).*$/`

**Notas:**
- `timeout 30`
- `priority 7`


### `skogul_Ok`

- `QuestHuntCompleted 21584 1752`
- `ConfigKey odin120_0 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `frus_Ok`

- `QuestHuntCompleted 21587 1753`
- `ConfigKey odin120_1 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `odin_tem03`

- `QuestActive 21590`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKeyNot odin120_0 3, odin120_1 3`
- `ConfigKey odin120_2 3`
- `InMapRegex /^(?!odin_tem03).*$/`

**Notas:**
- `timeout 30`
- `priority 7`


### `skeggioldMarron_Ok`

- `QuestHuntCompleted 21590 1754`
- `ConfigKey odin120_2 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `skeggioldAzul_Ok`

- `QuestHuntCompleted 21590 1755`
- `ConfigKey odin120_2 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `odin_Ok`

- `ConfigKey odin120_0 4, odin120_1 4, odin120_2 4`
- `ConfigKey quests100 2`

**Notas:**
- `timeout 30`
- `exclusive 1`


## Lago Do Abismo (120)


### `ativarAbyss120`

- `BaseLevel > 119`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey quests100 1`
- `ConfigKey abyss120_0 1, abyss120_1 1, abyss120_2 1`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 8`


### `dailyAbyss120`

- `QuestTimeOverdue 21641, 21644, 21647`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `ConfigKey quests100 1`
- `ConfigKey abyss120_0 2, abyss120_1 2, abyss120_2 2`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 8`


### `abyss_01`

- `QuestActive 21642`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKey abyss120_0 3`
- `InMapRegex /^(?!abyss_01).*$/`

**Notas:**
- `timeout 30`
- `priority 8`


### `ferusVerde_Ok`

- `QuestHuntCompleted 21642 1717`
- `ConfigKey abyss120_0 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `ferusEscarlate_Ok`

- `QuestHuntCompleted 21642 1714`
- `ConfigKey abyss120_0 3, abyss120_0 5`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `abyss_02`

- `QuestActive 21642, 21645`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKeyNot abyss120_0 3`
- `ConfigKey abyss120_0 5, abyss120_1 3`
- `InMapRegex /^(?!abyss_02).*$/`

**Notas:**
- `timeout 30`
- `priority 8`


### `acidusAzul_Ok`

- `QuestHuntCompleted 21645 1713`
- `ConfigKey abyss120_1 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `acidusDourado_Ok`

- `QuestHuntCompleted 21645 1716`
- `ConfigKey abyss120_1 3, abyss120_1 5`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `abyss_03`

- `QuestActive 21645, 21648`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `Eval ($::config{quests100} > 2)`
- `ConfigKeyNot abyss120_0 3, abyss120_0 5, abyss120_1 3`
- `ConfigKey abyss120_1 5, abyss120_2 3`
- `InMapRegex /^(?!abyss_03).*$/`

**Notas:**
- `timeout 30`
- `priority 8`


### `hydrolancer_Ok`

- `QuestHuntCompleted 21648 1720`
- `ConfigKey abyss120_2 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `abyss_Ok`

- `ConfigKey abyss120_0 4, abyss120_1 4, abyss120_2 4`
- `ConfigKey quests100 2`

**Notas:**
- `timeout 30`


# Quest de Classe


## Quests Aprendiz


### `init`

- `InMap iz_int, iz_int01, iz_int02, iz_int03, iz_int04`
- `ConfigKey 1sPassos 1`
- `BaseLevel == 1`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `primeirosPassos01`

- `QuestActive 21001`
- `ConfigKey 1sPassos 1`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `int_landPortal`

- `QuestActive 21001, 21008`
- `ConfigKey 1sPassos 1`
- `Console /Ainda há uma missão em progresso\./`

**Notas:**
- `timeout 2`
- `overrideAI 1`


### `primeirosPassos02`

- `QuestActive 21008`
- `InInventoryID 6008 > 1`

**Notas:**
- `timeout 15`


### `primeirosPassos03`

- `ConfigKey 1sPassos 2`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `primeirosPassos04`

- `QuestActive 21900`
- `ConfigKey 1sPassos 3`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `aulaDeConsu`

- `QuestActive 21901, 21902, 21903`
- `ConfigKey aulaDeConsu 1`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `aulaDeLoc`

- `QuestActive 21901, 21902, 21903`
- `ConfigKey aulaDeLoc 1`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `placasIz`

- `QuestActive 7474`
- `ConfigKey aulaDeLoc 1`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `aulaDeVenda`

- `QuestActive 21901, 21902, 21903`
- `ConfigKey aulaDeVenda 1`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 2`


### `lataVencida`

- `QuestActive 1240`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 2`


### `primeirosPassos05`

- `QuestActive 21901`
- `ConfigKey 1sPassos 3`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 4`


### `primeirosPassos06`

- `QuestActive 21902`
- `ConfigKey 1sPassos 3`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 5`


### `primeirosPassos07`

- `QuestActive 21903`
- `ConfigKey 1sPassos 3`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 5`


### `primeirosPassos08`

- `QuestActive 21904`
- `ConfigKey 1sPassos 3`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 5`


### `lunaticosOk`

- `QuestHuntCompleted 21905 1063`
- `InInventoryID 705 > 0`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `primeirosPassos09`

- `QuestActive 21906`
- `ConfigKey 1sPassos 3`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 5`


### `primeirosPassos10`

- `QuestActive 21907`
- `ConfigKey 1sPassos 3`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 5`


### `primeirosPassos11`

- `QuestActive 21908`
- `ConfigKey 1sPassos 3`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 99`


## Primeira Classe


### `primeiraClasse`

- `JobID 0`
- `JobLevel == 10`
- `Eval ($::config{classe1} > 0 && $::config{classe1} < 7)`

**Notas:**
- `priority 0`
- `exclusive 1`
- `timeout 30`


## Cavaleiro


### `goKnt01`

- `ConfigKey classe2 1`
- `ConfigKeyNot lockMap 0`
- `QuestInactive 9000`
- `QuestInactive 9001`
- `QuestInactive 9002`
- `QuestInactive 9003`
- `QuestInactive 9004`
- `QuestInactive 9005`
- `QuestInactive 9006`
- `QuestInactive 9007`
- `QuestInactive 9008`
- `QuestInactive 9009`
- `QuestInactive 9010`
- `QuestInactive 9011`
- `QuestInactive 9012`
- `JobLevel == 40..50`
- `JobLevel == $lvlC2`
- `JobID 1`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goKnt02`

- `QuestActive 9000`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `itemsKnt`

- `QuestActive 9001, 9002`
- `ConfigKeyNotExist itemsKnt`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `asasKnt`

- `QuestActive 9001, 9002`
- `ConfigKey itemsKnt 1`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `kntFulminante`

- `QuestActive 9001,9002,9006`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `JobID 1`
- `CurrentSP >= 15`
- `StatusInactiveHandle EFST_SIT`
- `MobNearDist /Gierath|Drainliar|Selvagem|Guerreiro|Grove|Poeira|Obeaune|Argos|Flora|Molusco|Magnólia|Argiope|Goblin|Frilldora/i < 2.5`

**Notas:**
- `timeout 1`
- `overrideAI 1`


### `pegarAsaBidoge`

- `QuestActive 9001`
- `CurrentHP >= 90%`
- `ConfigKey itemsKnt ok`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!mjo_dun02).*$/`
- `InInventoryID 1040 < 5, 7006 < 5`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `bigodeAnaoOk`

- `QuestActive 9001`
- `InMap mjo_dun02`
- `InInventoryID 7006 > 4`

**Notas:**
- `exclusive 1`
- `run-once 1`


### `asasDeMorcegoOk`

- `QuestActive 9001`
- `InMap mjo_dun02`
- `InInventoryID 7006 > 4`

**Notas:**
- `exclusive 1`
- `run-once 1`


### `pegarOrc`

- `QuestActive 9001`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!gef_fild10|gef_f10_).*$/`
- `InInventoryID 1040 > 4`
- `InInventoryID 7006 > 4`
- `InInventoryID 931 < 5`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `pegarCrina`

- `QuestActive 9001`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!mjolnir_07).*$/`
- `InInventoryID 1040 > 4`
- `InInventoryID 7006 > 4`
- `InInventoryID 931 > 4`
- `InInventoryID 1028 < 5`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `pegarLingua`

- `QuestActive 9001`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!cmd_fild01).*$/`
- `InInventoryID 1040 > 4`
- `InInventoryID 7006 > 4`
- `InInventoryID 931 > 4`
- `InInventoryID 1028 > 4`
- `InInventoryID 903 < 5`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `pegarTraca`

- `QuestActive 9001`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!mjolnir_12).*$/`
- `InInventoryID 1040 > 4`
- `InInventoryID 7006 > 4`
- `InInventoryID 931 > 4`
- `InInventoryID 1028 > 4`
- `InInventoryID 903 > 4`
- `InInventoryID 1057 < 5`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `ervaVerde`

- `QuestActive 9002`
- `InInventoryID 511 > 0`
- `StatusActiveHandle HEALTHSTATE_POISON`

**Notas:**
- `timeout 3`
- `overrideAI 1`


### `pegarFlorCarnivora`

- `QuestActive 9002`
- `CurrentHP >= 90%`
- `ConfigKey itemsKnt ok`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!mjolnir_10).*$/`
- `InInventoryID 1032 < 5`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `pegarPataInseto`

- `QuestActive 9002`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!mjolnir_05).*$/`
- `InInventoryID 1042 < 5`
- `InInventoryID 1032 > 4`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `pegarCasco`

- `QuestActive 9002`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!prt_fild04).*$/`
- `InInventoryID 1042 > 4`
- `InInventoryID 1032 > 4`
- `InInventoryID 946 < 5`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `pegarFrigideira`

- `QuestActive 9002`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!prt_fild09).*$/`
- `InInventoryID 1042 > 4`
- `InInventoryID 1032 > 4`
- `InInventoryID 946 > 4`
- `InInventoryID 7031 < 5`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `pegarSereia`

- `QuestActive 9002`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!iz_dun02).*$/`
- `InInventoryID 1042 > 4`
- `InInventoryID 1032 > 4`
- `InInventoryID 946 > 4`
- `InInventoryID 7031 > 4`
- `InInventoryID 950 < 5`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `pegarOstra`

- `QuestActive 9002`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!hu_fild06).*$/`
- `InInventoryID 1042 > 4`
- `InInventoryID 1032 > 4`
- `InInventoryID 946 > 4`
- `InInventoryID 7031 > 4`
- `InInventoryID 950 > 4`
- `InInventoryID 966 < 5`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `knt9001Ok`

- `QuestActive 9001`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InInventoryID 1040 > 4`
- `InInventoryID 7006 > 4`
- `InInventoryID 931 > 4`
- `InInventoryID 1028 > 4`
- `InInventoryID 903 > 4`
- `InInventoryID 1057 > 4`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `knt9002Ok`

- `QuestActive 9002`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InInventoryID 1042 > 4`
- `InInventoryID 950 > 4`
- `InInventoryID 1032 > 4`
- `InInventoryID 966 > 4`
- `InInventoryID 7031 > 4`
- `InInventoryID 946 > 4`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goKnt03`

- `QuestActive 9003`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goKnt04`

- `QuestActive 9004`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goKnt05`

- `QuestActive 9006`
- `CurrentHP >= 90%`
- `NotInMap job_knt`
- `ConfigKeyNotExist kntMobTest`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goKnt06`

- `QuestActive 9006`
- `ChatRoomNear /(ybqdBg|Waiting Room)/`
- `InMap job_knt`

**Notas:**
- `timeout 180`
- `exclusive 1`


### `kntMobTestOk`

- `Console /Amy Beatrice\./`
- `InMap job_knt`

**Notas:**
- `timeout 5`


### `goKnt07`

- `QuestActive 9006, 9008`
- `ConfigKeyDefined kntMobTest`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goKnt08`

- `QuestActive 9009, 9010`
- `NotInMap job_knt`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goKnt09`

- `QuestActive 9011`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goKnt10`

- `QuestActive 9012`

**Notas:**
- `timeout 30`
- `exclusive 1`


## Espadachim T


### `espadachimT`

- `JobLevel == 10`
- `ConfigKey classe1 1`
- `JobID 4001`

**Notas:**
- `timeout 30`
- `exclusive  1`


## Lorde


### `lord`

- `JobLevel == 50`
- `JobID 4002`

**Notas:**
- `timeout 30`
- `exclusive  1`


## Monge


### `goMonk01`

- `ConfigKey classe2 2`
- `ConfigKeyNot lockMap 0`
- `QuestInactive 3016`
- `QuestInactive 2020`
- `QuestInactive 2022`
- `QuestInactive 2023`
- `QuestInactive 2024`
- `QuestInactive 2026`
- `JobLevel == 40..50`
- `JobLevel == $lvlC2`
- `JobID 4`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goMonk02`

- `QuestActive 3016`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `itemsMonk`

- `QuestActive 3017, 3018, 3019, 3020, 3021, 3022, 3023`
- `ConfigKeyNotExist itemsMonk`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `asasMonk`

- `QuestActive 3017, 3018, 3019, 3020, 3021, 3022, 3023`
- `ConfigKey itemsMonk 1`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `pegarMucoMinhoca`

- `QuestActive 3017`
- `CurrentHP >= 90%`
- `ConfigKey itemsMonk 2`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!moc_fild17).*$/`
- `InInventoryID 1055 < 10, 938 < 5`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `pegarErvaVerde`

- `QuestActive 3017`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!prt_fild06).*$/`
- `InInventoryID 938 > 4`
- `InInventoryID 1055 > 9`
- `InInventoryID 511 < 20`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `monk3017Ok`

- `QuestActive 3017`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InInventoryID 938 > 4`
- `InInventoryID 1055 > 9`
- `InInventoryID 511 > 19`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `pegarMinério`

- `QuestActive 3018`
- `CurrentHP >= 90%`
- `ConfigKey itemsMonk 2`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!anthell01).*$/`
- `InInventoryID 1002 < 5`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `pegarErvaAzul`

- `QuestActive 3018`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!beach_dun3).*$/`
- `InInventoryID 1002 > 4`
- `InInventoryID 510 < 3`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `pegarYoyo`

- `QuestActive 3018`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!prt_fild03).*$/`
- `InInventoryID 1002 > 4`
- `InInventoryID 510 > 2`
- `InInventoryID 942 < 20`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `monk3018Ok`

- `QuestActive 3018`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InInventoryID 1002 > 4`
- `InInventoryID 510 > 2`
- `InInventoryID 942 > 19`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `pegarCaule`

- `QuestActive 3019`
- `CurrentHP >= 90%`
- `ConfigKey itemsMonk 2`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!gef_fild04).*$/`
- `InInventoryID 905 < 30`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `pegarVerme`

- `QuestActive 3019`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!anthell01).*$/`
- `InInventoryID 905 > 29`
- `InInventoryID 955 < 10`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `pegarJellopy`

- `QuestActive 3019`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!prt_fild01).*$/`
- `InInventoryID 905 > 29`
- `InInventoryID 955 > 9`
- `InInventoryID 909 < 5`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `monk3019Ok`

- `QuestActive 3019`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InInventoryID 905 > 29`
- `InInventoryID 955 > 9`
- `InInventoryID 909 > 4`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `pegarCascaMonk`

- `QuestActive 3020`
- `CurrentHP >= 90%`
- `ConfigKey itemsMonk 2`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!moc_fild13).*$/`
- `InInventoryID 935 < 20`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `pegarZargonio`

- `QuestActive 3020`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!cmd_fild02).*$/`
- `InInventoryID 935 > 19`
- `InInventoryID 912 < 5`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `pegarRija`

- `QuestActive 3020`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!iz_dun02).*$/`
- `InInventoryID 935 > 19`
- `InInventoryID 912 > 4`
- `InInventoryID 943 < 5`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `monk3020Ok`

- `QuestActive 3020`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InInventoryID 935 > 19`
- `InInventoryID 912 > 4`
- `InInventoryID 943 > 4`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `pegarCyfarAmarela`

- `QuestActive 3021`
- `CurrentHP >= 90%`
- `ConfigKey itemsMonk 2`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!cmd_fild02).*$/`
- `InInventoryID 7053 < 5, 508 < 10`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `pegarBranca`

- `QuestActive 3021`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!moc_pryd05).*$/`
- `InInventoryID 7053 > 4`
- `InInventoryID 508 > 9`
- `InInventoryID 509 < 10`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `monk3021Ok`

- `QuestActive 3021`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InInventoryID 7053 > 4`
- `InInventoryID 508 > 9`
- `InInventoryID 509 > 9`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `pegarDente`

- `QuestActive 3022`
- `CurrentHP >= 90%`
- `ConfigKey itemsMonk 2`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!moc_pryd01).*$/`
- `InInventoryID 913 < 10`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `pegarPataMonk`

- `QuestActive 3022`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!pay_fild07).*$/`
- `InInventoryID 913 > 9`
- `InInventoryID 948 < 5`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `pegarEsporo`

- `QuestActive 3022`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!mjolnir_06).*$/`
- `InInventoryID 913 > 9`
- `InInventoryID 948 > 4`
- `InInventoryID 7033 < 20`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `monk3022Ok`

- `QuestActive 3022`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InInventoryID 913 > 9`
- `InInventoryID 948 > 4`
- `InInventoryID 7033 > 19`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `pegarTeiaPata`

- `QuestActive 3022`
- `CurrentHP >= 90%`
- `ConfigKey itemsMonk 2`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!mjolnir_10).*$/`
- `InInventoryID 1042 < 20, 1025 < 10`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `pegarEspinho`

- `QuestActive 3022`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!mjolnir_01).*$/`
- `InInventoryID 1042 > 19`
- `InInventoryID 1025 > 9`
- `InInventoryID 1027 < 5`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `monk3023Ok`

- `QuestActive 3022`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InInventoryID 913 > 9`
- `InInventoryID 948 > 4`
- `InInventoryID 7033 > 19`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goMonk03`

- `QuestActive 3024`
- `QuestInactive 3026`
- `QuestInactive 3027`
- `QuestInactive 3028`
- `QuestInactive 3029`
- `QuestInactive 3031`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goMonk04`

- `QuestActive 3026`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goMonk05`

- `QuestActive 3027`
- `NotInMap job_monk`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goMonk06`

- `QuestActive 3027`
- `InMapRegex /job_monk/`
- `InInventoryID 1069 > 29, 1070 > 29`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goMonk07`

- `QuestActive 3029, 3031`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goMonk08`

- `QuestActive 3032`

**Notas:**
- `timeout 30`
- `exclusive 1`


## Noviço T


### `novicoT`

- `JobLevel == 10`
- `ConfigKey classe1 4`
- `JobID 4005`

**Notas:**
- `timeout 30`
- `exclusive  1`


## Mestre


### `mestre`

- `JobLevel == 50`
- `JobID 4005`

**Notas:**
- `timeout 30`
- `exclusive  1`


## Arruaceiro


### `goRogue01`

- `ConfigKey classe2 2`
- `ConfigKeyNot lockMap 0`
- `QuestInactive 2017`
- `QuestInactive 2020`
- `QuestInactive 2022`
- `QuestInactive 2023`
- `QuestInactive 2024`
- `QuestInactive 2026`
- `JobLevel == 40..50`
- `JobLevel == $lvlC2`
- `JobID 6`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `quiz01`

- `NpcMsg /(1)\. Escolha a habilidade necessária para aprender Túnel de Fuga\./i ################ ANTONIO JR?`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `delay 2`


### `quiz02`

- `NpcMsg /(1)\. Que monstro deixa cair um Gladius com slot\?/i`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `delay 2`


### `quiz03`

- `NpcMsg /(1)\. Qual é o aumento de Esquiva quando um Gatuno tem Perícia em Esquiva nível 10\?/i`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `delay 2`


### `goRogue02`

- `QuestActive 2017`

**Notas:**
- `timeout 120`
- `exclusive 1`


### `asasPingu`

- `QuestActive 2020`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InInventoryID 23280 < 20`
- `InInventoryID 508 < 10`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `stealPingu`

- `QuestActive 2020`
- `JobID 6`
- `CurrentSP >= 10`
- `InInventoryID 508 < 10`
- `MobNearDist /Pingu/i < 3`

**Notas:**
- `timeout 7`
- `delay 1`


### `pegarErvaAmarela`

- `QuestActive 2020`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!cmd_fild02).*$/`
- `InInventoryID 23280 > 19`
- `InInventoryID 508 < 10`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `stealRocker`

- `QuestActive 2020`
- `JobID 6`
- `CurrentSP >= 10`
- `InInventoryID 940 < 10`
- `MobNearDist /Rocker/i < 3`

**Notas:**
- `timeout 5`
- `delay 1`


### `pegarGafanhoto`

- `QuestActive 2020`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!moc_para0).*$/`
- `InInventoryID 508 > 9`
- `InInventoryID 940 < 10`

**Notas:**
- `timeout 30`
- `exclusive 1`
- `priority 1`


### `stealPeGrande`

- `QuestActive 2020`
- `JobID 6`
- `CurrentSP >= 10`
- `InInventoryID 948 < 10`
- `MobNearDist /(Pé-Grande|Bigfoot)/i < 3`

**Notas:**
- `timeout 6`
- `delay 1`


### `pegarPata`

- `QuestActive 2020`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!pay_fild07).*$/`
- `InInventoryID 508 > 9`
- `InInventoryID 940 > 9`
- `InInventoryID 948 < 10`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `stealBesouro`

- `QuestActive 2020`
- `JobID 6`
- `CurrentSP >= 10`
- `InInventoryID 935 < 10`
- `MobNearDist /(Besouro-Chifre|Horn)/i < 3`

**Notas:**
- `timeout 6`
- `delay 1`


### `pegarCasca`

- `QuestActive 2020`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!pay_fild09).*$/`
- `InInventoryID 508 > 9`
- `InInventoryID 935 < 10`
- `InInventoryID 940 > 9`
- `InInventoryID 948 > 9`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `escapeCast`

- `QuestActive 2020`
- `MobNearDist /(Salgueiro|Pingu)/ < 8`
- `Console /conjurando (Esfera d'Água|Waterball|Lanças de Fogo|Fire Bolt)/i`

**Notas:**
- `timeout 3`


### `goRogue03`

- `QuestActive 2020`
- `CurrentHP >= 90%`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InInventoryID 508 > 9`
- `InInventoryID 935 > 9`
- `InInventoryID 940 > 9`
- `InInventoryID 948 > 9`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goAraghamJr`

- `QuestActive 2022, 2026`
- `CurrentHP >= 90%`
- `ConfigKeyNotExist antonioJr, holgrenJr`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goAntonioJr`

- `QuestActive 2023, 2026`
- `CurrentHP >= 90%`
- `ConfigKeyNotExist araghamJr, holgrenJr`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`

**Notas:**
- `timeout 30`
- `exclusive 1`


### `goHolgrenJr`

- `QuestActive 2024, 2026`
- `CurrentHP >= 90%`
- `ConfigKeyNotExist araghamJr, antonioJr`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`

**Notas:**
- `timeout 30`
- `exclusive 1`


## Gatuno T


### `gatunoT`

- `JobLevel == 10`
- `ConfigKey classe1 6`
- `JobID 4001`

**Notas:**
- `timeout 30`
- `exclusive  1`


### `placaPryd`

- `NpcMsg /Por acaso está procurando pela Guilda dos Gatunos\?/`
- `InMapRegex /moc_prydb1/`

**Notas:**
- `timeout 3`


## Desordeiro


### `stalker`

- `JobLevel == 50`
- `JobID 4007`

**Notas:**
- `timeout 30`
- `exclusive  1`


## Renascer


### `renascer`

- `QuestInactive 5160`
- `BaseLevel == 99`
- `JobID 7,8,9,10,11,12,13,14,15,16,17,18,19,20,21`
- `ConfigKey reborn 1, reborn 2`

**Notas:**
- `exclusive  1`
- `timeout 30`


### `asas99`

- `QuestActive 5160`
- `InInventoryID 601 < 30`

**Notas:**
- `exclusive 1`
- `timeout 180`
- `priority 2`


### `goLivroFugitivo`

- `QuestActive 5160`
- `Eval ((grep {$_ =~ /^(?:sellAuto|buyAuto|storageAuto|repairAuto)(?:_.*)?$/} @::ai_seq) == 0)`
- `InMapRegex /^(?!yuno_fild12).*$/`
- `InInventoryID 601 > 29`

**Notas:**
- `exclusive 1`
- `priority 2`
- `timeout 30`


### `livroFugitivoOk`

- `InInventoryID 6586 > 0`
- `CheckOnAI manual, auto`

**Notas:**
- `exclusive  1`
- `timeout 30`


### `aprendizT`

- `QuestActive 1000`
- `CheckOnAI manual, auto`

**Notas:**
- `exclusive 1`
- `timeout 30`


# Rotas

## Rota 1


### `rota00a`

- `BaseLevel == 1..7`
- `ConfigKey rota 1, rota 2`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lockMap prt_fild08`
- `InMapRegex /^(?!moc_para0).*$/`

**Notas:**
- `run-once 1`
- `exclusive 1`


### `rota01a`

- `BaseLevel == 8..28`
- `ConfigKey rota 1, rota 2`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lockMap pay_fild08`
- `InMapRegex /^(?!moc_para0).*$/`

**Notas:**
- `run-once 1`
- `exclusive 1`


### `rota02a`

- `BaseLevel == 29..32`
- `ConfigKey rota 1, rota 2`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lockMap pay_fild07`
- `InMapRegex /^(?!moc_para0).*$/`

**Notas:**
- `run-once 1`
- `exclusive 1`


### `rota03a`

- `BaseLevel == 33..39`
- `ConfigKey rota 1, rota 2`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lockMap pay_fild09`
- `InMapRegex /^(?!moc_para0).*$/`

**Notas:**
- `run-once 1`
- `exclusive 1`


### `rota04a`

- `BaseLevel == 40..47`
- `ConfigKey rota 1`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lockMap iz_dun01`
- `InMapRegex /^(?!moc_para0).*$/`

**Notas:**
- `run-once 1`
- `exclusive 1`


### `rota05a`

- `BaseLevel == 48..55`
- `ConfigKey rota 1`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lockMap iz_dun02`
- `InMapRegex /^(?!moc_para0).*$/`

**Notas:**
- `run-once 1`
- `exclusive 1`


### `rota06a`

- `BaseLevel == 56..68`
- `ConfigKey rota 1`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lockMap moc_fild17`
- `InMapRegex /^(?!moc_para0).*$/`

**Notas:**
- `run-once 1`
- `exclusive 1`


### `rota07a`

- `BaseLevel == 69..78`
- `ConfigKey rota 1`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lockMap yuno_fild08`
- `InMapRegex /^(?!moc_para0).*$/`

**Notas:**
- `run-once 1`
- `exclusive 1`


### `rota08a`

- `BaseLevel == 79..89`
- `ConfigKey rota 1`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lockMap yuno_fild11`
- `InMapRegex /^(?!moc_para0).*$/`

**Notas:**
- `run-once 1`
- `exclusive 1`


### `rota09a`

- `BaseLevel == 90..99`
- `ConfigKey rota 1`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lockMap ve_fild07`
- `InMapRegex /^(?!moc_para0).*$/`

**Notas:**
- `run-once 1`
- `exclusive 1`


## Rota 2


### `rota04b`

- `BaseLevel == 40..47`
- `ConfigKey rota 2`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lockMap gef_fild10`
- `InMapRegex /^(?!moc_para0).*$/`

**Notas:**
- `run-once 1`
- `exclusive 1`


### `rota05b`

- `BaseLevel == 48..55`
- `ConfigKey rota 2`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot  lockMap orcsdun01`
- `InMapRegex /^(?!moc_para0).*$/`

**Notas:**
- `run-once 1`
- `exclusive 1`


### `rota06b`

- `BaseLevel == 56..64`
- `ConfigKey rota 2`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lockMap mjolnir_08`
- `InMapRegex /^(?!moc_para0).*$/`

**Notas:**
- `run-once 1`
- `exclusive 1`


### `rota07b`

- `BaseLevel == 65..76`
- `ConfigKey rota 2`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lockMap mjolnir_04`
- `InMapRegex /^(?!moc_para0).*$/`

**Notas:**
- `run-once 1`
- `exclusive 1`


### `rota08b`

- `BaseLevel == 77..89`
- `ConfigKey rota 2`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lockMap gef_fild08`
- `InMapRegex /^(?!moc_para0).*$/`

**Notas:**
- `run-once 1`
- `exclusive 1`


### `rota09b`

- `BaseLevel == 90..99`
- `ConfigKey rota 2`
- `ConfigKeyNot lockMap 0`
- `ConfigKeyNot lockMap gef_fild06`
- `InMapRegex /^(?!moc_para0).*$/`

**Notas:**
- `run-once 1`
- `exclusive 1`
