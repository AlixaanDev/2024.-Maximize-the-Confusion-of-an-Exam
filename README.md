# 2024.-Maximize-the-Confusion-of-an-Exam
class Solution:
    def maxConsecutiveAnswers(self, answerKey: str, k: int) -> int:
        l = 0
        charDic = {}
        res = 0

        for r in range(len(answerKey)):
            charDic[answerKey[r]] = 1 + charDic.get(answerKey[r], 0)

            while (r-l+1) - max(charDic.values()) > k:
                charDic[answerKey[l]] -= 1
                l+=1
            res = max(res, r-l+1)
        return res
