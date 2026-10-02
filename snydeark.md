# Snydeark: Claude Code i projektmappen

**Den hårde regel:** ingen identificerbare patientdata i mappen eller i en samtale med Claude.

## Første gang: installér

Claude Code kræver et betalt abonnement (Pro eller højere). Gratisversionen er ikke nok.

- **Mac:** åbn **Terminal** og indsæt
  `curl -fsSL https://claude.ai/install.sh | bash`
- **Windows:** installér først **Git for Windows** (git-scm.com). Åbn derefter **PowerShell** og indsæt
  `irm https://claude.ai/install.ps1 | iex`

Første gang I skriver `claude`, åbner en browser, hvor I logger ind med jeres Claude-konto.

**R:** Claude skriver analysekoden i R. Vil I køre den selv, skal R være installeret (cran.r-project.org).

## Hver gang

1. **Mac:** åbn Terminal, skriv `cd ` (med mellemrum), træk projektmappen ind i vinduet, og tryk Enter.
   **Windows:** højreklik på projektmappen i Stifinder, og vælg *Åbn i Terminal*.
2. Skriv `claude` og tryk Enter.
3. Skriv `start`. Første gang forklarer Claude mappen og hjælper jer med at udfylde `plan.md`. Senere fortæller den, hvor I slap.

## Det, I skriver til Claude

Skriv gerne på dansk. Kommandoerne herunder virker, som de står, og I kan ændre dem frit.

| Når I vil ... | Skriv |
| :--- | :--- |
| Se, hvor I er | `start` |
| Skrive protokollen | `draft the next protocol section` |
| Et bestemt afsnit | `draft the protocol section on outcomes` |
| Få jeres kommentarer udført | `address the XX comments in protocol/04_participants.md` |
| Se, hvad der mangler | `what is still missing from the protocol?` |
| Låse protokollen | `the protocol is final, lock it` |
| Skrive analyseplanen | `draft the next SAP section` |
| Forberede et møde med en statistiker | `write a statistician brief` |
| Få en second opinion | `get a second opinion on the sample size section` |
| Tjekke en reference | `check this reference in CrossRef: ...` |
| Skrive artiklen | `draft the next manuscript section` |
| Tjekke påstande | `run claim-check on manuscript/04_discussion.md` |
| Gøre et mødereferat til opgaver | `turn feedback/2026-10-14_meeting.txt into todo items` |

## Taster

- **Esc** stopper Claude midt i noget.
- **Pil op** henter jeres sidste besked.
- **/** viser alle kommandoer og skills.
- **/clear** starter en ny samtale. Filerne er uændrede.
- **Ctrl+C** to gange lukker Claude Code.

## Når Claude spørger om lov

Læs, hvad den vil gøre. **1** = ja, **2** = ja, og spørg ikke igen om det samme, **3** = nej, og skriv, hvad den skal gøre i stedet. I tvivl? Vælg nej og bed om en forklaring.

## Sådan skriver I i filerne

Åbn filerne i en teksteditor (VS Code, eller TextEdit i *ren tekst*). **Ikke i Word.**

- **Afsnit** (`protocol/`, `sap/`, `manuscript/`): ret direkte i teksten. Claude ser jeres ændringer og lærer jeres præferencer af dem.
- **Kommentarer** til Claude skrives i teksten mellem to XX, gerne på dansk:
  `We will include children aged 1 to 5. XX skal det være 6 mdr. til 5 år? XX`
  Skriv derefter `address the XX comments in ...`.
- **`XX TO FILL: ... XX`** er Claudes pladsholder for et faktum, den mangler. Skriv faktum ind i stedet, eller svar i samtalen.
- **`plan.md`:** beslutninger skrives under *Decisions* med dato og begrundelse. Slet ikke gamle beslutninger.
- **`todo.md`:** `- [ ] **[Y]** opgave` for jer, `[C]` for Claude, jeres initialer for medforfattere. Sæt `x` i `[ ]`, når den er løst.
- **`style.md`:** tilføj jeres egne regler nederst, også gammel kritik fra reviewere.
- **`references.bib`:** når I selv har læst kilden, skriv over posten:
  `% CHECKED 2026-10-14 ANK: RCT, n=84. Effekt ved 12 mdr., ikke 24.`
  Kun I skriver `CHECKED`-linjer.
- **`feedback/`:** læg mødereferater og reviews her, med dato i filnavnet.
- **`advisors/`:** gem svar fra en anden model ved siden af prompten, fx `sample_size_review_copilot.txt`.
- **`data/`:** kun anonymiserede data, eller blot en note om, hvor data ligger. Claude kan ikke åbne datafilerne, kun analysescripts kan.
