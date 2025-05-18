import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("Most Profitable Movies of All Time - Top 500 Movies.csv")
df.columns = df.columns.str.strip()
print("First 5 rows of the dataset:")
print(df.head())

print("\nColumn names:")
print(df.columns.tolist())

print("\nDataset info:")
print(df.info())

print("\nDescriptive statistics:")
print(df.describe())
# قراءة البيانات
# import pandas as pd
# df = pd.read_csv("/kaggle/input/netflix-shows/netflix_titles.csv")
# عرض أول 5 صفوف
# df.head()
# معلومات عن الأعمدة
# df.info()
# وصف عددي للبيانات
# df.describe()
print("\nMissing values in each column:")
print(df.isnull().sum())
# التحقق من القيم المفقودة
# df.isnull().sum()

top_10 = df.sort_values(by='worldwide gross (m)', ascending=False).head(10)
plt.figure(figsize=(12,6))
sns.barplot(x='worldwide gross (m)', y='title', data=top_10, palette='viridis')
plt.title('Top 10 Movies by Worldwide Gross')
plt.xlabel('Worldwide Gross (in millions)')
plt.ylabel('Movie Title')
plt.tight_layout()
plt.show()

plt.figure(figsize=(8,6))
sns.scatterplot(data=df, x='budget  (millions)', y='worldwide gross (m)', hue='decade')
plt.title('Budget vs Worldwide Gross')
plt.xlabel('Budget (in millions)')
plt.ylabel('Worldwide Gross (in millions)')
plt.legend(title='Decade')
plt.tight_layout()
plt.show()

plt.figure(figsize=(8,6))
sns.histplot(df['budget  (millions)'], bins=30, kde=True, color='teal')
plt.title('Distribution of Movie Budgets')
plt.xlabel('Budget (in millions)')
plt.ylabel('Number of Movies')
plt.tight_layout()
plt.show()
