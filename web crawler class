import java.util.regex.Pattern;
import java.util.regex.Matcher;

public class WebCrawler { 

    public static void main(String[] args) { 

        // timeout connection after 500 miliseconds
        System.setProperty("sun.net.client.defaultConnectTimeout", "500");
        System.setProperty("sun.net.client.defaultReadTimeout",    "1000");

        String s = args[0];

        // list of web pages to be examined
        Queue<String> q = new Queue<String>();
        q.enqueue(s);

        // existence symbol table of examined web pages
        SET<String> set = new SET<String>();
        set.add(s);

        // breadth first search crawl of web
        while (!q.isEmpty()) {
            String v = q.dequeue();
            System.out.println(v);

            In in = new In(v);

            if (!in.exists()) continue;

            String input = in.readAll();


            String  regexp  = "http://(\\w+\\.)*(\\w+)";
            Pattern pattern = Pattern.compile(regexp);
            Matcher matcher = pattern.matcher(input);

            // find and print all matches
            while (matcher.find()) {
                String w = matcher.group();
                if (!set.contains(w)) {
                    q.enqueue(w);
                    set.add(w);
                }
            }

        }
   }
}
