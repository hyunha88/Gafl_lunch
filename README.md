package gafl_lunch;

import java.io.IOException;
import java.util.Scanner;

import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;
import org.jsoup.nodes.Element;

public class Gafl_lunch {

public static void main(String[] args) {
	
	System.out.println("날짜를 입력하세요");
	Scanner in = new Scanner(System.in);
	String date = in.nextLine();	
	String url = "http://www.gafl.hs.kr/?act=lunch.main2&month=" + date + "&mcode=141910";
	
	try {
		Document doc = Jsoup.connect(url).get();
		//System.out.println(doc.html());
		Element span1 = doc.selectFirst("#morning .menuName span");
		System.out.println("조식 : " + span1.html());
		Element span2 = doc.selectFirst("#lunch .menuName span");
		System.out.println("중식 : " + span2.html());
		Element span3 = doc.selectFirst("#dinner .menuName span");
		System.out.println("석식 : " + span3.html());
	}
	catch(IOException e) {
		System.out.println("오류");
	}

	
	
	
	
	
}

}
