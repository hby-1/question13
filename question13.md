# 将标题首字母大写

给你一个字符串 `title` ，它由单个空格连接一个或多个单词组成，每个单词都只包含英文字母。请你按以下规则将每个单词的首字母 **大写** ：

- 如果单词的长度为 `1` 或者 `2` ，所有字母变成小写。
- 否则，将单词首字母大写，剩余字母变成小写。
请你返回 **大写后** 的 `title` 。

## 示例 1：

>### 输入：
>title = "capiTalIze tHe titLe"
>### 输出：
>"Capitalize The Title"
>### 解释：
>由于所有单词的长度都至少为 3 ，将每个单词首字母大写，剩余字母变为小写。

## 示例 2：
>### 输入：
>title = "First leTTeR of EACH Word"
>### 输出：
>"First Letter of Each Word"
>### 解释：
>单词 "of" 长度为 2 ，所以它保持完全小写。其他单词长度都至少为 3 ，所以其他单词首字母大写，剩余字母小写。

## 代码：
1.

    public class Solution {
        public string CapitalizeTitle(string title) {
            // 将字符串按空格拆分成单词数组
            string[] words = title.Split(' ');

            // 使用 StringBuilder 构建最终的字符串
            var result = new System.Text.StringBuilder();

            // 遍历每个单词
            for (int i = 0; i < words.Length; i++) {
                if (words[i].Length > 2) {
                    // 如果单词长度大于2，则首字母大写，其余部分小写
                    result.Append(char.ToUpper(words[i][0]));
                    result.Append(words[i].Substring(1).ToLower());
                } else {
                    // 如果单词长度小于等于2，则整个单词转换为小写
                    result.Append(words[i].ToLower());
                }

                // 添加空格（除了最后一个单词后面）
                if (i < words.Length - 1) {
                    result.Append(' ');
                }
            }

            // 返回构建的字符串
            return result.ToString();
        }
    }
2.

    public class Solution {
        public string CapitalizeTitle(string title) {
            string[] words=title.Split(' ');
            for(int i=0;i<words.Length;i++){
                if(words[i].Length>2){
                    words[i]=words[i].ToLower();
                    words[i]=char.ToUpper(words[i][0]) + words[i].Substring(1);
                }
                else{
                    words[i]=words[i].ToLower();
                }
            }
            return string.Join(' ',words);
        }
    }
3.

    public class Solution {
        public string CapitalizeTitle(string title) {
            StringBuilder sb = new StringBuilder();
            string[] words = title.Split(" ");
            int wordsCount = words.Length;
            for (int i = 0; i < wordsCount; i++) {
                String word = words[i];
                if (sb.Length > 0) {
                    sb.Append(" ");
                }
                int wordLength = word.Length;
                sb.Append(wordLength > 2 ? char.ToUpper(word[0]) : char.ToLower(word[0]));
                for (int j = 1; j < wordLength; j++) {
                    sb.Append(char.ToLower(word[j]));
                }
            }
            return sb.ToString();
        }
    }

