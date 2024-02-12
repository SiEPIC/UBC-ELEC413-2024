#Design By Andrey Abushakhmanov

from pya import *

 
def design_Andrey(cell, cell_y, inst_wg1, inst_wg2, inst_wg3, waveguide_type):
    
    # load functions
    from SiEPIC.scripts import connect_pins_with_waveguide, connect_cell
    ly = cell.layout()
    library = ly.technology().name

    # took it from Lucas
    cell_taper = ly.create_cell('ebeam_taper_350nm_2000nm_te1310', library)

    # returns: ['text', 'font_name', 'layer', 'mag', 'inverse', 'bias', 'cspacing', 'lspacing', 'eff_cw', 'eff_ch', 'eff_lw', 'eff_dr', 'font']
    from SiEPIC.utils import get_technology_by_name
    TECHNOLOGY = get_technology_by_name(library)
    cell_text = ly.create_cell('TEXT', "Basic", {
        'text':cell.name,
        'layer': TECHNOLOGY['M1'],
        'mag': 30,
         })
    if not cell_text:
        raise Exception ('Cannot load text label cell; please check the script carefully.')
    cell.insert(CellInstArray(cell_text.cell_index(), Trans(Trans.R0, 25000,125000)))                

    # load the cells from the PDK
    # my parameters
    cell_bragg = ly.create_cell('ebeam_pcell_bragg_grating', library, {
        'number_of_periods':10,
        'grating_period': 0.272,
        'corrugation_width': 0.05,
        'wg_width': 0.35,
        'sinusoidal': False})
    if not cell_bragg:
        raise Exception ('Cannot load Bragg grating cell; please check the script carefully.')

    # Define a waveguide to connect the big side of the tapers
    waveguide_type_mm = 'Multimode Strip TE 1310 nm, w=2000 nm'

    # Define the parameters of the move
    height = 20000
    width = 200000

    # instantiate y-branch (attached to input waveguide)
    inst_y1 = connect_cell(inst_wg1, 'opt2', cell_y, 'opt2')
    
    # instantiate Bragg grating (attached to y branch)
    inst_bragg1 = connect_cell(inst_y1, 'opt1', cell_bragg, 'opt1')

    ########## Initiate all the tapers and wveguides ########### 
    inst_taper1 = connect_cell(inst_bragg1, 'opt2', cell_taper, 'opt')
    
    inst_taper2 = connect_cell(inst_taper1, 'opt2', cell_taper, 'opt2')
    inst_taper2.transform(Trans(width,0))
    
    connect_pins_with_waveguide(inst_taper1, 'opt2', inst_taper2, 'opt2', waveguide_type=waveguide_type_mm)

    inst_taper3 = connect_cell(inst_taper1, 'opt2', cell_taper, 'opt2')
    inst_taper3.transform(Trans(width,height))

    connect_pins_with_waveguide(inst_taper2, 'opt', inst_taper3, 'opt', waveguide_type=waveguide_type)

    inst_taper4 = connect_cell(inst_taper3, 'opt2', cell_taper, 'opt2')
    inst_taper4.transform(Trans(-width,0))

    connect_pins_with_waveguide(inst_taper3, 'opt2', inst_taper4, 'opt2', waveguide_type=waveguide_type_mm)

    inst_taper5 = connect_cell(inst_taper3, 'opt2', cell_taper, 'opt2')
    inst_taper5.transform(Trans(-width,height))

    connect_pins_with_waveguide(inst_taper4, 'opt', inst_taper5, 'opt', waveguide_type=waveguide_type)
    
    inst_taper6 = connect_cell(inst_taper5, 'opt2', cell_taper, 'opt2')
    inst_taper6.transform(Trans(width,0))

    connect_pins_with_waveguide(inst_taper5, 'opt2', inst_taper6, 'opt2', waveguide_type=waveguide_type_mm)

    inst_taper7 = connect_cell(inst_taper5, 'opt2', cell_taper, 'opt2')
    inst_taper7.transform(Trans(width,height))

    connect_pins_with_waveguide(inst_taper6, 'opt', inst_taper7, 'opt', waveguide_type=waveguide_type)

    inst_taper8 = connect_cell(inst_taper7, 'opt2', cell_taper, 'opt2')
    inst_taper8.transform(Trans(-width,0))

    connect_pins_with_waveguide(inst_taper7, 'opt2', inst_taper8, 'opt2', waveguide_type=waveguide_type_mm)

    inst_taper9 = connect_cell(inst_taper7, 'opt2', cell_taper, 'opt2')
    inst_taper9.transform(Trans(-width,height))

    connect_pins_with_waveguide(inst_taper8, 'opt', inst_taper9, 'opt', waveguide_type=waveguide_type)

    inst_taper10 = connect_cell(inst_taper9, 'opt2', cell_taper, 'opt2')
    inst_taper10.transform(Trans(width,0))
    
    connect_pins_with_waveguide(inst_taper9, 'opt2', inst_taper10, 'opt2', waveguide_type=waveguide_type_mm)

    inst_taper11 = connect_cell(inst_taper9, 'opt2', cell_taper, 'opt2')
    inst_taper11.transform(Trans(width,height))

    connect_pins_with_waveguide(inst_taper10, 'opt', inst_taper11, 'opt', waveguide_type=waveguide_type)

    inst_taper12 = connect_cell(inst_taper11, 'opt2', cell_taper, 'opt2')
    inst_taper12.transform(Trans(-width,0))

    connect_pins_with_waveguide(inst_taper11, 'opt2', inst_taper12, 'opt2', waveguide_type=waveguide_type_mm)

    inst_taper13 = connect_cell(inst_taper11, 'opt2', cell_taper, 'opt2')
    inst_taper13.transform(Trans(-width,height))

    connect_pins_with_waveguide(inst_taper12, 'opt', inst_taper13, 'opt', waveguide_type=waveguide_type)
    
    inst_taper14 = connect_cell(inst_taper13, 'opt2', cell_taper, 'opt2')
    inst_taper14.transform(Trans(width,0))
   
    connect_pins_with_waveguide(inst_taper13, 'opt2', inst_taper14, 'opt2', waveguide_type=waveguide_type_mm)

    inst_taper15 = connect_cell(inst_taper13, 'opt2', cell_taper, 'opt2')
    inst_taper15.transform(Trans(width,height))

    connect_pins_with_waveguide(inst_taper14, 'opt', inst_taper15, 'opt', waveguide_type=waveguide_type)

    inst_taper16 = connect_cell(inst_taper15, 'opt2', cell_taper, 'opt2')
    inst_taper16.transform(Trans(-width,0))

    connect_pins_with_waveguide(inst_taper15, 'opt2', inst_taper16, 'opt2', waveguide_type=waveguide_type_mm)

    inst_taper17 = connect_cell(inst_taper15, 'opt2', cell_taper, 'opt2')
    inst_taper17.transform(Trans(-width,height))

    connect_pins_with_waveguide(inst_taper16, 'opt', inst_taper17, 'opt', waveguide_type=waveguide_type)

    inst_taper18 = connect_cell(inst_taper17, 'opt2', cell_taper, 'opt2')
    inst_taper18.transform(Trans(width,0))
    
    connect_pins_with_waveguide(inst_taper17, 'opt2', inst_taper18, 'opt2', waveguide_type=waveguide_type_mm)

    inst_taper19 = connect_cell(inst_taper17, 'opt2', cell_taper, 'opt2')
    inst_taper19.transform(Trans(width,height))

    connect_pins_with_waveguide(inst_taper18, 'opt', inst_taper19, 'opt', waveguide_type=waveguide_type)

    inst_taper20 = connect_cell(inst_taper19, 'opt2', cell_taper, 'opt2')
    inst_taper20.transform(Trans(-width,0))

    connect_pins_with_waveguide(inst_taper19, 'opt2', inst_taper20, 'opt2', waveguide_type=waveguide_type_mm)

    inst_taper21 = connect_cell(inst_taper19, 'opt2', cell_taper, 'opt2')
    inst_taper21.transform(Trans(-width,height))

    connect_pins_with_waveguide(inst_taper20, 'opt', inst_taper21, 'opt', waveguide_type=waveguide_type)

    inst_taper22 = connect_cell(inst_taper21, 'opt2', cell_taper, 'opt2')
    inst_taper22.transform(Trans(width,0))    

    connect_pins_with_waveguide(inst_taper21, 'opt2', inst_taper22, 'opt2', waveguide_type=waveguide_type_mm)

    inst_bragg2 = connect_cell(inst_taper22, 'opt', cell_bragg, 'opt2')

    connect_pins_with_waveguide(inst_bragg2, 'opt1', inst_wg2, 'opt1', waveguide_type=waveguide_type, turtle_A = [20, -90, 132.7, 90], error_min_bend_radius=False)
    ########## Finish initiateing all the tapers and wveguides ########### 


    # Outer WaveGuide Connection 
    try:
        connect_pins_with_waveguide(inst_y1, 'opt3', inst_wg3, 'opt1', 
            waveguide_type='Strip TE 1310 nm, w=350 nm (core-clad)', 
            turtle_A = [10,-90,215,-90,355,90] )
    except:    
        connect_pins_with_waveguide(inst_y1, 'opt3', inst_wg3, 'opt1', 
            waveguide_type='Strip TE 1310 nm, w=385 nm (core-clad)', 
            turtle_A = [10,-90,215,-90,355,-90] )

    return inst_wg1, inst_wg2, inst_wg3
