package org.prime;

import org.prime.Configuration.Configs;
import org.prime.Services.CrawlerService;
import org.prime.Services.FileMangerService;

import java.io.IOException;
import java.util.*;


public class Controller {
    public static void main(String[] args) {
        CrawlerService crawlerService = new CrawlerService();
        ArrayList<String> urls = FileMangerService.readList(
                Configs.inputFile,
                0,
                -1);
        
        int noOfUrls = urls.size();
        String output = "[";

        for(int i = 0; i < noOfUrls; i++) {
            String url = urls.get(i);
            String[] data = url.split(" ");
            String jsonData = crawlerService.getJsonDataFromUrl(data[0], data[1], data[2], data[3]);
            if(i > 0) output += ",";
            output += "\n" + jsonData;
        }

        output += "\n" + "]";

        try {
            FileMangerService.writeString(Configs.outputFile, output);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
