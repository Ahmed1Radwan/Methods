# Methods
SHEET 2
Name : احمد حمدى ابراهيم رضوان مصطفى
ID : 4 


// our main class
public class LinkedListNode {
	int value;
	LinkedListNode next;
	
	
	public int getValue(LinkedListNode node) {
		return node.value;
	}
	public LinkedListNode getNext(LinkedListNode node) {
		return node.next;
	}
}

/////////////////////////////////

// static Methods

1-   public static double[] summary (LinkedListNode head) {
		double[] ans = new double[] {0,0,0,0,0};
		LinkedListNode temp = head;
		if(temp == null || temp.next == null) {
			return head;
		}else {
		int count=0;
		ans[3] = temp.value;
		ans[4] = temp.value;
		while(temp != null) {
			ans[0] += temp.value;
			if(temp.value > ans[3]) {
				ans[3] = temp.value;
			}else if(temp.value < ans[4]) {
				ans[4] = temp.value;
			}
			count++;
			temp = temp.next;
		}
		
		ans[1] = ans[0] / (double)count;
		temp = head.next;
		int medianCount=0;
		if(count%2 == 0) {
			while(temp != null) {
				if(medianCount == (count/2)-1) {
					ans[2] = temp.value;
					temp = temp.next;
					ans[2] += temp.value;
					ans[2] = ans[2] / 2.0;
					break;
				}
				temp = temp.next;
				medianCount++;
			}
		}else {
			while(temp != null) {
				if(medianCount == (count/2)) {
					ans[2] = temp.value;
					break;
				}
				temp = temp.next;
				medianCount++;
			}
		}
		
		return ans;
	  }
	}
  
2- public static LinkedListNode reverse(LinkedListNode head) {
		LinkedListNode current = head;
		LinkedListNode prev = null;
		LinkedListNode next;
		while(current != null) {
			next = current.next;
			current.next = prev;
			prev = current;
			current = next;
		}
		head = prev;
		return head;
	}

3- public static LinkedListNode evenIndexedElements(LinkedListNode head) {
		LinkedListNode ans;
		LinkedListNode p;
		ans = head;
		p=ans;
		
		int i=1;
		while(head.next != null) {
			head = head.next;
			if((i%2) == 0) {
				ans.next = head;
				ans = ans.next;
			}
			i++;
		}
		ans.next = null;
		return p;
	}
  
4- public static LinkedListNode insertionSort(LinkedListNode head) {
		if(head == null || head.next == null) {
	        return head;
		}
		LinkedListNode current = head;
		LinkedListNode pivot = current;
		head =head.next;
		
		 while(head != null) {
			 pivot =current;
			 while(pivot != head) {
				 if(pivot.value > head.value) {
					 int temp = head.value;
					 head.value=pivot.value;
					 pivot.value=temp;
				 }else {
					 pivot = pivot.next;
				 }
			 }
			 head = head.next;
		 }
		 return current;
	}
  
5- public static LinkedListNode merge_Sort(LinkedListNode head) {
			if(head == null || head.next == null) {
		        return head;
			}
			LinkedListNode middle = getMiddle(head);
			LinkedListNode left = head;
			LinkedListNode right = middle.next;
			middle.next = null;
			
			return result(merge_Sort(left),merge_Sort(right));
		}
	public static LinkedListNode result(LinkedListNode l ,LinkedListNode r) {
		LinkedListNode temp = new LinkedListNode();
		LinkedListNode current;
		
		for( current  = temp; l != null && r != null; current = current.next)
	    {
	        if(l.value <= r.value) 
	        {
	            current.next = l; 
	            l = l.next; 
	        }
	        else
	        { 
	            current.next = r;
	            r = r.next; 
	        }

	    }
	    current.next = (l == null) ? r :l;
	    return temp.next;
	}
	public static LinkedListNode getMiddle(LinkedListNode head)
	{
	    if(head == null) 
	        return head;

	    LinkedListNode temp1 = head, temp2 = head;

	    while(temp2.next != null && temp2.next.next != null)
	    {
	    	temp1 = temp1.next;
	        temp2 = temp2.next.next;
	    }
	    return temp1;
	}
  
6- public static LinkedListNode removeCentralNode(LinkedListNode head) {
		LinkedListNode temp = head;
		int count=0;
		while(temp!=null) {
			count++;
			temp = temp.next;
		}
		temp =head;
		int counter=0;
		if(count == 2 ) {
			return temp.next;
		}else if(count == 1) {
			return temp.next;
		}
		if(count%2 == 0) {
			while(temp!=null) {
				if(counter == (count/2)-2) {
					LinkedListNode p = temp;
					LinkedListNode q = p.next;
					p.next = q.next;
					break;
				}
				counter++;
				temp = temp.next;
			}
		}else {
			while(temp!=null) {
				if(counter == (count/2)-1) {
					LinkedListNode p = temp;
					LinkedListNode q = p.next;
					p.next = q.next;
					break;
				}
				counter++;
				temp=temp.next;
			}
		}
		return head;
	}
  
7- public static boolean palindrome(LinkedListNode head) {
		LinkedListNode p=head;
		LinkedListNode q=head;
		LinkedListNode start;
		while(true) {
			p = p.next.next;
			if(p.next == null) {
				start = q.next.next;
				break;
			}
			if(p==null) {
				start =q.next;
				break;
			}
			q=q.next;
		}
		q.next = null;
		LinkedListNode reverseSecond = reverse(start);
		while(reverseSecond !=null) {
			if(reverseSecond.value != head.value) {
				return false;
			}
			reverseSecond = reverseSecond.next;
			head = head.next;
		}
		return true;
	}
  
