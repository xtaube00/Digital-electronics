# Lab 4: YOUR_FIRSTNAME LASTNAME

### Seven-segment display decoder

1. Listing of VHDL stimulus process from testbench file (`tb_hex_7seg.vhd`) with asserts. Verify all input combinations. Always use syntax highlighting, meaningful comments, and follow VHDL guidelines:

```vhdl
    p_stimulus : process
    begin
        report "Stimulus process started" severity note;
        -- First test case
        s_hex <= "0000"; wait for 50 ns;
        assert (s_seg = "0000001")
        report "Input combination 0000 FAILED" severity error;

        s_hex <= "0001"; wait for 50 ns;
        assert (s_seg = "1001111")
        report "Input combination 0001 FAILED" severity error;
        
        s_hex <= "0010"; wait for 50 ns;
        assert (s_seg = "0010010")
        report "Input combination 0010 FAILED" severity error;
        
        s_hex <= "0011"; wait for 50 ns;
        assert (s_seg = "0000110")
        report "Input combination 0011 FAILED" severity error;
        
        s_hex <= "0100"; wait for 50 ns;
        assert (s_seg = "1001100")
        report "Input combination 0100 FAILED" severity error;
        
        s_hex <= "0101"; wait for 50 ns;
        assert (s_seg = "0100100")
        report "Input combination 0101 FAILED" severity error;
        
        s_hex <= "0110"; wait for 50 ns;
        assert (s_seg = "0100000")
        report "Input combination 0110 FAILED" severity error;
        
        s_hex <= "0111"; wait for 50 ns;
        assert (s_seg = "0001111")
        report "Input combination 0111 FAILED" severity error;
        
        s_hex <= "1000"; wait for 50 ns;
        assert (s_seg = "0000000")
        report "Input combination 1000 FAILED" severity error;
        
        s_hex <= "1001"; wait for 50 ns;
        assert (s_seg = "0000100")
        report "Input combination 1001 FAILED" severity error;
        
        s_hex <= "1010"; wait for 50 ns;
        assert (s_seg = "0001000")
        report "Input combination 1010 FAILED" severity error;
        
        s_hex <= "1011"; wait for 50 ns;
        assert (s_seg = "1100000")
        report "Input combination 1011 FAILED" severity error;
        
        s_hex <= "1100"; wait for 50 ns;
        assert (s_seg = "1000010")
        report "Input combination 1100 FAILED" severity error;
        
        s_hex <= "1101"; wait for 50 ns;
        assert (s_seg = "0110000")
        report "Input combination 1101 FAILED" severity error;
        
        s_hex <= "1110"; wait for 50 ns;
        assert (s_seg = "0110000")
        report "Input combination 1110 FAILED" severity error;
        
        s_hex <= "1111"; wait for 50 ns;
        assert (s_seg = "0111000")
        report "Input combination 0000 FAILED" severity error;


        report "Stimulus process finished" severity note;

       
        wait;
    end process p_stimulus;
```

2. Screenshot with simulated time waveforms. Always display all inputs and outputs (display the inputs at the top of the image, the outputs below them) at the appropriate time scale!

   ![your figure](04.png)

### LED(7:4) indicators

1. Listing of LEDs(7:4) part of VHDL architecture from source file `top.vhd`. Try to write logic functions as simple as possible. Always use syntax highlighting, meaningful comments, and follow VHDL guidelines:

   --------------------------------------------------------------------
   -- Experiments on your own: LED(7:4) indicators
   LED4 : process (SW)
            begin
                if (SW = "0000") then
                    LED(4) <= '1';
                else
                    LED(4) <= '0';
                end if;
            end process LED4;

   
   LED5 : process (SW)
            begin
                if (SW < b"1001") then
                    LED(5) <= '0';
                else
                    LED(5) <= '1';
                end if;
            end process LED5;

   LED6 : process (SW)
            begin
                if (SW(0) = '1') then
                    LED(6) <= '1';
                else
                    LED(6) <= '0';
                end if;
            end process LED6;

   LED7 : process (SW)
            begin            
                case SW is
                    when "0001" =>
                    LED(7) <= '0';
                    when "0010" =>
                    LED(7) <= '0';
                    when "0100" =>
                    LED(7) <= '0';
                    when "1000" =>
                    LED(7) <= '0';
                    when others =>
                    LED(7) <= '1';
            end case;
            end process LED7;

end Behavioral;
