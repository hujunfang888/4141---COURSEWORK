# 4141course-work-for-pca
conda env list
conda activate base
vcftools --version

#在系统中搜索文件
find ~/ -name "LAB_NEN_ODN.clean_BI.ann.3mbChr5.vcf.gz" 

#切换到文件所在目录
cd "/Users/phoebe/Desktop/LIFE4141_coursework_resources 2024-2025-20241223/Data, helpful code and files"
#创建样本txt
nano LAB_population.txt
LAB_004
LAB_1
LAB_2
LAB_300
LAB_4
LAB_400
LAB_5
LAB_500 

nano NEN_population.txt
NEN_001
NEN_003
NEN_200
NEN_300
NEN_4
NEN_5
NEN_6   
 
#运行vcf
vcftools --gzvcf LAB_NEN_ODN.clean_BI.ann.3mbChr5.vcf.gz \
         --max-missing 0.8 \
         --maf 0.05 \
         --weir-fst-pop LAB_population.txt \
         --weir-fst-pop NEN_population.txt \
         --fst-window-size 5000 \
         --fst-window-step 5000 \
         --out LAB_vs_NENT_Fst
      
      
#提取high Fst value作为候选选择性清扫区域
awk 'NR>1 {print $0}' LAB_vs_NENT_Fst.windowed.weir.fst | sort -k5,5nr | head -n $(echo "$(wc -l < LAB_vs_NENT_Fst.windowed.weir.fst) * 0.01" | bc)


#保存将前 1% 的高 Fst 值区域：
awk 'NR>1 {print $0}' LAB_vs_NENT_Fst.windowed.weir.fst | sort -k5,5nr | head -n $(echo "$(wc -l < LAB_vs_NENT_Fst.windowed.weir.fst) * 0.01" | bc) > top_Fst_regions.txt



#与基因组注释文件比对
#安装bedtools
conda install -c bioconda bedtools
