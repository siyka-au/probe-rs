Debug: When the stack unwind encounters stack frames with no return register (LR/RA) values, it will not try to unwind them. This happens when reset handler trampolines (e.g. cortex-m-rt) explicitly clears those values to prevent debuggers from unwinding past the `main_trampoline`. Attempting to unwind past these frames results in undefined behavior.