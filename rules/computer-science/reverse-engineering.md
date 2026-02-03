# Reverse Engineering Rules

When analyzing external binaries, protocols, or proprietary code:

## Clean Room Methodology (Mandatory)

1. **Never copy code directly** - Generate functional specifications instead
2. **Separate analysis from implementation** - Use the Chinese Wall technique
3. **Document behavior, not implementation** - Describe what it does, not how
4. **Maintain audit trail** - Track all sources and specifications

## Specification Requirements

- Write specifications in natural language or formal notation
- Document observable behavior: inputs, outputs, state transitions
- Avoid any reference to original variable names or code structure
- Have specifications reviewed before implementation

## Legal Framework

- Use only legitimately obtained materials
- Never use leaked source code or documentation
- Follow precedents: IBM BIOS (Columbia/Phoenix), WINE, Dolphin Emulator

## Implementation

- Implementation team must have no exposure to original code
- Test against behavioral specifications, not original implementation
- Document everything for legal defensibility

**For detailed methodology:** Use `/reverse-engineering` skill
