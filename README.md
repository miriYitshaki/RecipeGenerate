# RecipeGenerate
Recipes Generation Using Personal Nutrition Information


Three model
  Baseline
   train
      !python3 -u -m recipe_gen.models.baseline.train --data-dir DataModified/ --batch-size 32 --vocab-emb-size 300 --calorie-emb-size 5 --nhid 256 --nlayers 2 --lr 1e-3 --epochs 1 --annealing-rate 0.9 --save OUTPUTS/ --ingr-emb --ingr-gru --exp-name baseline
   Test 
      !python3 -m recipe_gen.models.baseline.test --data-dir DataModified/ --model-path OUTPUTS/model_baseline_eX.pt --vocab-emb-size 300 --calorie-emb-size 5 --nhid 256 --nlayers 2 --ingr-emb --ingr-gru --ingr-emb-size 10 --save-dir OUTPUTS/ --batch-size 32 --ingr-gru
  User Prefrence
      Same with basline userpref as model
  User nutrition prefrence (***************** New Model we added )
    Train
      !python3 -u -m recipe_gen.models.user_nutri_pref.train --data-dir DataTemp50K/ --batch-size 38 --vocab-emb-size 300 --tech-emb-size 50 --calorie-emb-size 6 --nhid 256 --nlayers 2 --lr 1e-3 --epochs 7 --annealing-rate 0.9 --save OUTPUT50FNutri/ --ingr-emb --ingr-gru --exp-name usernutri
    Test   
      !python3 -u -m recipe_gen.models.user_nutri_pref.test --data-dir DataModified/ --model-path OUTPUT50FNutri/model_usernutri_eX.pt --batch-size 38 --vocab-emb-size 300  --calorie-emb-size 6 --nhid 256 --nlayers 2 --ingr-emb --ingr-gru --ingr-emb-size 10 --save-dir OUTPUT50FNutri/ --batch-size 36 --ingr-gru
      
