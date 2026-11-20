# Material de teste do Zelo

| Pasta | Conteúdo | Quem preenche |
|---|---|---|
| `stt/roteiro_gravacao.csv` | 20 frases, falante, gênero, faixa etária e ruído de cada áudio | já pronto (confirmar o gênero do F3) |
| `stt/audios/` | os 20 áudios gravados pelo grupo (`stt_01.wav` ... `stt_20.wav`) | **grupo grava** |
| `llm/perguntas_avaliacao.csv` | 30 perguntas com resposta esperada: 20 do tema (2 sem resposta na base), 5 de continuação e 5 fora do escopo | já pronto |
| `tts/frases_tts.csv` | 10 respostas típicas para sintetizar | já pronto |
| `tts/avaliacao_tts.csv` | planilha de notas (1 a 5) de naturalidade e clareza | **3 avaliadores preenchem** |
| `e2e/conversas.csv` | 10 conversas com 3 turnos, com continuação e recusa | já pronto |
| `e2e/audios/` | (opcional) gravações reais dos turnos, `c01_t1.wav` ... | opcional |

## Como gravar os 20 áudios do STT

1. **Três vozes diferentes** (o enunciado pede no mínimo 3):
   * F1: Gabriel (masculino, 18 a 29 anos), áudios 01 a 07
   * F2: Mayara (feminino, 18 a 29 anos), áudios 08 a 14
   * F3: uma pessoa de 60 anos ou mais (é a persona do Zelo e permite analisar viés por idade), áudios 15 a 20. Preencha o gênero dela na coluna `genero`.
2. **Cinco áudios com ruído de fundo** já estão marcados no roteiro (`ruido = sim`): 06 (TV ligada), 07 (rua/trânsito), 13 (música), 14 (conversa ao fundo) e 20 (ventilador). Grave esses com o ruído de verdade acontecendo.
3. Leia a frase da coluna `referencia` **exatamente como está escrita**, em ritmo natural. Números como "156" podem ser falados normalmente ("cento e cinquenta e seis").
4. Pode gravar no iPhone (Gravador/Memos de Voz) ou no Mac (QuickTime > Nova gravação de áudio). Exporte e renomeie para `stt_01.m4a`, `stt_02.m4a`... O script aceita `.wav`, `.m4a`, `.mp3`, `.ogg` e `.webm`.
5. Coloque tudo em `material_teste/stt/audios/`.

## Consentimento dos falantes (LGPD)

Esses áudios são o único material de voz que o projeto guarda, porque são a prova da avaliação exigida pelo enunciado. Por isso:

* cada pessoa que gravar assina (ou aceita por mensagem) o termo em `docs/termo_consentimento_gravacao.md`;
* os falantes aparecem só como F1, F2 e F3, sem nome, nos resultados;
* as frases são fictícias e não contêm dados pessoais;
* os áudios podem ser apagados ao fim da avaliação da disciplina, a pedido de qualquer falante.

## Avaliação do TTS

Depois de rodar `python -m eval.eval_tts gerar`, cada avaliador (A1, A2, A3) escuta os 10 arquivos de `tts/audios/` e dá duas notas de 1 a 5 na planilha `tts/avaliacao_tts.csv`:

* **Naturalidade**: 1 = robótico, 5 = parece uma pessoa falando.
* **Clareza**: 1 = não entendi, 5 = entendi tudo de primeira, inclusive números e siglas.

Dica: peça para a pessoa 60+ ser um dos avaliadores. Ela é o público do assistente.
