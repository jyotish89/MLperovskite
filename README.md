# MLperovskite
Perovskite Band-Gap Uncertainty Pipeline
Reproducible pipeline for data/master_composition_bandgap.csv. Run the scripts in order (each is checkpointed and reads/writes data/*.pkl or
data/*.joblib, so any stage can be re-run independently once earlier
checkpoints exist):
pip install -r requirements.txtpython scripts/run_validation.py          
# phase 1: clean + auditpython scripts/run_tuning.py              
# phase 2: tune + fit once, grouped CVpython scripts/run_repeated_benchmark.py  
# phase 3: 20-seed UQ benchmark, 4 methodspython scripts/run_lobo.py                
# phase 4: LOBO + noveltypython scripts/run_sensitivity.py        
# phase 5: Mondrian + GPR ladderspython scripts/build_report.py            
# phase 6: figures, tables, manuscript
Outputs land under results/{figures,tables,markdown,latex}/.

