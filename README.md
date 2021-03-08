# TranspositionCipher



package binaryTrees;
import java.util.Scanner;

public class TranspositionCipher {


	public static void main (String args[]){
		//rail fence transposition cipher
		System.out.println("What message do you want to encode?");
		Scanner first = new Scanner(System.in);
		String p = first.nextLine();
		String prompt = "";
		for(int z=0;z<p.length();z++) {
			if(!(p.substring(z,z+1).matches("[!? ]"))){
				prompt+=p.substring(z,z+1);
			}
		}
		int rob = 0;
		String top = "";
		String mid = "";
		String bot = "";
		boolean up=true;
		for(int y=0;y<prompt.length();y++) {
			if(rob==0) {
				top+=prompt.substring(y,y+1);
				rob++;
				up = true;
			}
			else if(rob==1) {
				mid+=prompt.substring(y,y+1);
				if(up==true) {
					rob++;
				}
				else {
					rob--;
				}
			}
			else if(rob==2) {
				bot+=prompt.substring(y,y+1);
				rob--;
				up = false;
			}
		}
		String bob = top + mid + bot;
		//System.out.println("HERE " + top + " " + mid + " " + bot);
		String done ="";
		for(int ab=0;ab<bob.length();ab++) {
			if(ab%5==0 && ab!=0) {
				done+=" ";
			}
			done+=bob.substring(ab,ab+1);
		}
		System.out.println(done);
		System.out.println("What message do you want to decode?");
		Scanner second = new Scanner(System.in);
		String zaphod = second.nextLine();
		String str = "";
		for(int z=0;z<zaphod.length();z++) {
			if(!(zaphod.substring(z,z+1).matches("[!? ]"))){
				str+=zaphod.substring(z,z+1);
			}
		}
		String t="";String m="";String b="";
		t=str.substring(0,str.length()/4);
		m=str.substring(str.length()/4, str.length()*3/4);
		b=str.substring(str.length()*3/4);
		if(str.length()%4!=0) {
			t=str.substring(0,str.length()/4+1);
			m=str.substring(str.length()/4+1, str.length()*3/4);
		}
		//System.out.println("AND HERE " + t + " " + m + " " + b);
		String doubledone="";
		for(int y=0;m.length()>0 && b.length()>0 && t.length()>0;y++) {
			System.out.print(t.substring(0,1) + m.substring(0,1) + b.substring(0,1));
			t = t.substring(1);
			m = m.substring(1);
			b = b.substring(1);
			if(m.length()>0) {
				System.out.print(m.substring(0,1));
				m=m.substring(1);
			}
		}
		if(t.length()>0) {
			System.out.print(t);
			if(m.length()>0) {
				System.out.print(m);
			}
			if(b.length()>0) {
				System.out.print(b);
			}
		}
	}
}
