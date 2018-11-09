注：
白板写尽量使用递归版，这样的代码简洁

- 链表反转
```
递归版:
public static Node Reverse1(ListNode head) {
  // head看作是前一结点，head.getNext()是当前结点，reHead是反转后新链表的头结点
  if (head == null || head.next == null) {
    return head;// 若为空链或者当前结点在尾结点，则直接还回
  }
  ListNode reHead = Reverse1(head.next);// 先反转后续节点head.getNext()
  head = head.next.next;// 将当前结点的指针域指向前一结点
  head.next = null;// 前一结点的指针域令为null;
  return reHead;// 反转后新链表的头结点
}
非递归版:
private ListNode reverseList(ListNode l){
    if(l == null || l.next == null)
        return l;
    ListNode cur = l;
    ListNode pos = l.next;
    cur.next = null;
    while(pos!= null){
        ListNode temp = pos.next;
        pos.next = cur;
        cur = pos;
        pos = pos.next;
    }
    return cur;
}
```

- 链表长度
```
public int get_length(Node head) {
    if (head == null) {
        return -1;
    }
    int length = 0;
    current = head;
    while(current != null) {
        length++;
        current = current.next;
    }
    return length;
}
```
