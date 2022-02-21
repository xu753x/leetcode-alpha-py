# Leetcode using AI :robot:

Leetcode自动代码生成。使用预训练的模型生成leetcode的python代码题解。

## 使用方式

下载预训练好的模型 

git clone https://huggingface.co/gagan3012/project-code-py-small 或 git clone https://huggingface.co/gagan3012/project-code-py-neo

修改 app.py 中 tokenizer 和 model 路径到下载后的预训练模型目录

pip install -r requirements.txt 如果有包版本依赖问题，升级对应的包 pip install --upgrade 

在本机下执行 streamlit run app.py ，无GPU环境也可以运行。

网页模板演示效果见 https://huggingface.co/spaces/gagan3012/project-code-py

## 后续版本演进

训练模型并调参

自动代码提交验证

# Using AI to Generate LeetCode solutions

GPT-2 Model for Leetcode Questions in python  New demo here: https://huggingface.co/spaces/gagan3012/project-code-py

**Note**: the Answers might not make sense in some cases because of the bias in GPT-2 Current accuracy is capped at 90%. 

**Contribtuions:** If you would like to make the model/UI better contributions (Issues/PRs) are welcome Check out [CONTRIBUTIONS](https://github.com/gagan3012/project-code-py/blob/master/.github/CONTRIBUTIONS.md) 

**How I built this** : [Linkedin](https://www.linkedin.com/feed/update/urn:li:activity:6775934721827459072/) 

### 📢 Favour:

It would be highly motivating, if you can STAR⭐ this repo if you find it helpful. New improvements incoming!

## Model

Two models have been developed for different use cases and they can be found at https://huggingface.co/gagan3012

The model weights can be found here: [GPT-2](https://huggingface.co/gagan3012/project-code-py) and [DistilGPT-2](https://huggingface.co/gagan3012/project-code-py-small)

The model has been trained using **Weights and Biases (Wandb)** and **PyTorch**

GPT Neo model: https://huggingface.co/gagan3012/project-code-py-neo

### Example usage:
```python
from transformers import AutoTokenizer, AutoModelWithLMHead

tokenizer = AutoTokenizer.from_pretrained("project-code-py-small")

model = AutoModelWithLMHead.from_pretrained("project-code-py-small")

or

tokenizer = AutoTokenizer.from_pretrained("project-code-py-neo")

model = AutoModelWithLMHead.from_pretrained("project-code-py-neo")

```

## Example results:

### Question:

```
Write a function to delete a node in a singly-linked list. You will not be given access to the head of the list, instead you will be given access to the node to be deleted directly. It is guaranteed that the node to be deleted is not a tail node in the list.
```

### Answer:

```python
""" Write a function to delete a node in a singly-linked list. You will not be given access to the head of the list, instead you will be given access to the node to be deleted directly. It is guaranteed that the node to be deleted is not a tail node in the list.

For example,
a = 1->2->3
b = 3->1->2
t = ListNode(-1, 1)

Note: The lexicographic ordering of the nodes in a tree matters. Do not assign values to nodes in a tree.
Example 1:

Input: [1,2,3]
Output: 1->2->5
Explanation: 1->2->3->3->4, then 1->2->5[2] and then 5->1->3->4.


Note:

The length of a linked list will be in the range [1, 1000].
Node.val must be a valid LinkedListNode type.
Both the length and the value of the nodes in a linked list will be in the range [-1000, 1000].
All nodes are distinct.
"""
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def deleteNode(self, head: ListNode, val: int) -> None:
        """
        BFS
        Linked List
        :param head: ListNode
        :param val: int
        :return: ListNode
        """
        if head is not None:
            return head
        dummy = ListNode(-1, 1)
        dummy.next = head
        dummy.next.val = val
        dummy.next.next = head
        dummy.val = ""


s1 = Solution()
print(s1.deleteNode(head))
print(s1.deleteNode(-1))
print(s1.deleteNode(-1))

   ```
