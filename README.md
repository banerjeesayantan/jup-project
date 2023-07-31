# jup-project
School result project
#pip install numpy
#pip install pandas
#pip install matplotlib
#pip install seaborn

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("Expanded_data_with_more_features.csv")
print(df.head())

df.describe()

df.info()

df.isnull().sum()

# Drop unnamed column





# change weekly study hours column

df["WklyStudyHours"] = df["WklyStudyHours"].str.replace("05-Oct","5-10")
df.head()

# gender distribution

plt.figure(figsize= (4,4))
ax = sns.countplot(data = df, x = "Gender")
ax.bar_label(ax.containers[0])
plt.title("Gender Distribution")
plt.show()

# from the above chart we have analysed that:
# the number of females in the data is more than the number of males

gb = df.groupby("ParentEduc").agg({"MathScore":'mean',"ReadingScore":'mean',"WritingScore":'mean'})
print(gb)

plt.figure(figsize= (4,4))
sns.heatmap(gb, annot = True)
plt.title("Relationship between Parent's Education and Student's Score")            
plt.show()

#from the above chart we have concluded that the education of the parents have a good impact

gb1 = df.groupby("ParentMaritalStatus").agg({"MathScore":'mean',"ReadingScore":'mean',"WritingScore":'mean'})
print(gb1)

plt.figure(figsize= (4,4))
sns.heatmap(gb1, annot = True)
plt.title("Relationship between Parent's Marital Status and Student's Score") 
plt.show()

#from the above chart we have concluded that there is no/negligible impact on the 
#student's score due to their parent's marital status

sns.boxplot(data = df, x ="MathScore")
plt.show()

sns.boxplot(data = df, x ="ReadingScore")
plt.show()

sns.boxplot(data = df, x ="WritingScore")
plt.show()

print(df["EthnicGroup"].unique())
[nan 'group c' 'group B' 'group A' 'group D' 'group E']

# Distribution of Ethnic Groups

groupA = df.loc[(df['EthnicGroup'] == "group A")].count()
groupB = df.loc[(df['EthnicGroup'] == "group B")].count()
groupC = df.loc[(df['EthnicGroup'] == "group C")].count()
groupD = df.loc[(df['EthnicGroup'] == "group D")].count()
groupE = df.loc[(df['EthnicGroup'] == "group E")].count()

l = ["groupA", "groupB", "groupC", "groupD", "groupE"]
mlist = [groupA["EthnicGroup"], groupB["EthnicGroup"], groupC["EthnicGroup"], groupD["EthnicGroup"], groupE["EthnicGroup"]]
print(mlist)
plt.pie(mlist, labels =l, autopct = "%1.2f%%")
plt.title("Distribution of Ethnic Groups")
plt.show()



ax = sns.countplot(data = df, x = 'EthnicGroup')
ax.bar_label(ax.containers[0])







