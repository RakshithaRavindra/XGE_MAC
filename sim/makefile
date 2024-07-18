all: clean compile simulate
 
compile:
	vlib work;
	vlog -sv \
	-l mac_compile.log \
	-f mac_compile.f
 
simulate:
	vsim \
	work.xgemac_top \
	-voptargs=+acc=npr \
	+UVM_TESTNAME=xgemac_normal_test \
	-l mac_sim.log \
	-c -do "log -r /*; add wave -r /*; run -all;  exit" \
	-wlf waveform.wlf

view:
	vsim -view waveform.wlf
 
clean:
	rm -rf transcript *.vcd *.wlf work/ *.log > mac_sim.log
