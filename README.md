# RecipeGenerate
Recipes Generation Using Personal Nutrition Information
Data https://www.kaggle.com/shuyangli94/food-com-recipes-and-user-interactions

Project report in the pdf 


Three model

  1. Baseline
  
   train
   
      !python3 -u -m recipe_gen.models.baseline.train --data-dir DataModified/ --batch-size 32 --vocab-emb-size 300 --calorie-emb-size 5 --nhid 256 --nlayers 2 --lr 1e-3 --epochs 1 --annealing-rate 0.9 --save OUTPUTS/ --ingr-emb --ingr-gru --exp-name baseline
      
   Test 
   
      !python3 -m recipe_gen.models.baseline.test --data-dir DataModified/ --model-path OUTPUTS/model_baseline_eX.pt --vocab-emb-size 300 --calorie-emb-size 5 --nhid 256 --nlayers 2 --ingr-emb --ingr-gru --ingr-emb-size 10 --save-dir OUTPUTS/ --batch-size 32 --ingr-gru
      
  2. User Prefrence
      Same with basline userpref as model
      
 3. User nutrition prefrence (***************** New Model we added )
    Train
    
      !python3 -u -m recipe_gen.models.user_nutri_pref.train --data-dir DataTemp50K/ --batch-size 38 --vocab-emb-size 300 --tech-emb-size 50 --calorie-emb-size 6 --nhid 256 --nlayers 2 --lr 1e-3 --epochs 7 --annealing-rate 0.9 --save OUTPUT50FNutri/ --ingr-emb --ingr-gru --exp-name usernutri
      
    Test   
    
      !python3 -u -m recipe_gen.models.user_nutri_pref.test --data-dir DataModified/ --model-path OUTPUT50FNutri/model_usernutri_eX.pt --batch-size 38 --vocab-emb-size 300  --calorie-emb-size 6 --nhid 256 --nlayers 2 --ingr-emb --ingr-gru --ingr-emb-size 10 --save-dir OUTPUT50FNutri/ --batch-size 36 --ingr-gru
      

Based on:
@inproceedings{majumder-etal-2019-generating,
    title = "Generating Personalized Recipes from Historical User Preferences",
    author = "Majumder, Bodhisattwa Prasad  and
      Li, Shuyang  and
      Ni, Jianmo  and
      McAuley, Julian",
    booktitle = "EMNLP",
    year = "2019",
    url = "https://www.aclweb.org/anthology/D19-1613",
    doi = "10.18653/v1/D19-1613",
    pages = "5975--5981",
}
