## Buffer Overflow
Reference 
https://github.com/joshua17sc/Buffer-Overflows
https://github.com/Tib3rius/Pentest-Cheatsheets/blob/master/exploits/buffer-overflows.rst
https://www.coengoedegebure.com/buffer-overflow-attacks-explained/


1. Spiking  - Find the vulnerable part of program.
   - Need to use `generic_send_tcp` tool
   - Usage
   ```bash
	./generic_send_tcp host port spike_script SKIPVAR SKIPSTR
	./generic_send_tcp host port spike_script.spk 0 0
   ```
    - spike_script.spk
	```bash
	s_readline();
	s_string("STATS ");
	s_string_variable("0");
   ```
2. Fuzzing  - Send bunch of characters to break it.
3. Finding the Offset - If we break it, then on which point we break it. 
4. Overwriting the EIP - Use the offset to overwrite the EIP.
5. Finding Bad Characters
6. Finding the Right Module 
7. Generating Shellcode - 
8. Root!