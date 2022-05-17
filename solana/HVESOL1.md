## Missing Signer Checks
&nbsp;
| |  |
| ----------- | ----------- |
| Identifier | HVESOL1 |
| Name | MissingSignerChecks |
| Description| if an instruction should only be available to a restricted set of entities, but the program does not verify that the call has been signed by the appropriate entity. |
| Severity | High |
| Tags | wasm, solana |
| Example | [Go to example](#Example) |
| Recomendation | [Recomendation](#Recomendation) |
| Related | - |
&nbsp;

### Example
```bash
use anchor_lang::prelude::*;

declare_id!("Fg6PaFpoGXkYsidMpWTK6W2BeZ7FEfcYkg476zPFsLnS");

#[program]
pub mod signer_authorization_insecure {
    use super::*;

    pub fn log_message(ctx: Context<LogMessage>) -> ProgramResult {
        msg!("GM {}", ctx.accounts.authority.key().to_string());
        Ok(())
    }
}

#[derive(Accounts)]
pub struct LogMessage<'info> {
    authority: AccountInfo<'info>,
}
```
### Recomendation
