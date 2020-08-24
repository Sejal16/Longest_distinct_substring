# Longest_distinct_substring
package string;
import java.util.*;

public class Long_distinct_Substring {

	public static void main(String[] args) {
Scanner sc=new Scanner(System.in);
String str=sc.next();
approch1(str);  //O(n^3)
approch2(str); //O(n^2)
approch3(str); //O(n)
	}

	

	public static void approch1(String str) {
		int n=str.length();
		int res=0;
		for(int i=0;i<n;i++)
	
		{
			for(int j=i;j<n;j++)
			{
				if(distinct(str,i,j)==true) 
						res=Math.max(res,j-i+1);
					
				}
			}
		System.out.println(res);
		}
		
	public static boolean distinct(String str, int i, int j) {
		boolean fre[]=new boolean[256];
		for(int k=i;k<=j;k++)
		{
			if(fre[str.charAt(k)]==true)
				return false;
			else
				fre[str.charAt(k)]=true;
		}
		return true;
	

	}
public static void approch2(String str) {
		
	int n=str.length();
	int res=0;
	
	for(int i=0;i<n;i++)
	{boolean fre[]=new boolean[256];
		for(int j=i;j<n;j++)
		{
			if(fre[str.charAt(j)]==true)
				break;
			else {
				fre[str.charAt(j)]=true;
			res=Math.max(res, j-i+1);
		}
	}
//		fre[str.charAt(i)]=false;
		}
	System.out.println(res);
	}

	public static void approch3(String str) {
		int n=str.length();
		int res=0;
		int prev[]=new int[256];
		Arrays.fill(prev, -1);
		int i=0;
		for(int j=0;j<n;j++) {
			i=Math.max(i, prev[str.charAt(j)]+1);
			int len=j-i+1;
			res=Math.max(res,len);
			prev[str.charAt(j)]=j;
		}
		System.out.println(res);
	}
}
