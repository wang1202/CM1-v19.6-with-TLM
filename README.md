# CM1-v19.6-with-TLM
Contributors: 
George Bryan, 
Aaron Wang

---------------------

This is the CM1 code with two-layer model (TLM) used for idealized tornado simulation in Wang et al. (2022).  To modify the setting for TLM:

1. Balaras' or Cabot's eddy viscosity
    code: src/turb.F, lines 5556
    tlm_nu  =  1: Balaras'
    tlm_nu  =  2: Cabot's

2. Levels within the wall layer
    code: src/cm1.F, line 964
    nktlm = 20: 20 U-levels in the wall layer.

The main code is written in the subroutine "tlmcode" in src/turb.F.  

Note that the moving domain (imove = 1 in run/namelist.input) has been taken into consideration in the tlmcode subroutine (search "umove", "vmove", or "if( imove.eq.1 )then") but has not been tested.  A linear decrease may be needed for the initial condition (set in src/init3d.F) to avoid extremely high shear causing numerical instability near the surface.  
