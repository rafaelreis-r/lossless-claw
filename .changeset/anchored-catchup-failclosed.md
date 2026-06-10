---
"@martian-engineering/lossless-claw": patch
---

Two reconcile hardening fixes for conversations that previously wedged or silently lost coverage. (1) An anchored reconcile whose missing tail exceeds the flood cap no longer blocks permanently: on the live afterTurn lane (runtime session matches the conversation) it imports a cap-bounded contiguous prefix of the missing tail per turn — order preserved, checkpoint held back — so repeated turns converge instead of looping the partial-overlap import-cap abort forever (the loop reported on #822). Other lanes keep the all-or-nothing block. (2) afterTurn now fails closed when the transcript reconcile throws: previously the initialized in-sync default persisted the live batch and refreshed the checkpoint to EOF past history that was never reconciled; the turn is now skipped (the transcript retains it for the next successful reconcile).
