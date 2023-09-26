/**
 * 
 * @author (Nesma Abouzaid) 
 * @version (07/03/2023)
 */

import edu.duke.*;
import java.io.File;
import org.apache.commons.csv.*;
//Download the zip file first "nc_weather (2).zip"
public class Part1 {
    public CSVRecord coldestHourInFile(CSVParser parser){
        //This method gives me the csv record with the lowest temperature in a file.
        CSVRecord minTemp = null; //null is really important when iterating CSVRecord files to do comparisons. If I try 0, I will get an error as it is a csvrecord variable type, not an int or double.
         for (CSVRecord currentRow : parser){
           minTemp = lowestOfTwo(currentRow, minTemp);
        }
        return minTemp;
    }
    
    public CSVRecord lowestOfTwo(CSVRecord currentRow,CSVRecord minTemp){
         if (minTemp == null) {
                minTemp = currentRow;
            }
            else{
                 double currentTemp = Double.parseDouble(currentRow.get("TemperatureF"));
                 double minTempNum = Double.parseDouble(minTemp.get("TemperatureF"));
                if (currentTemp < minTempNum && currentTemp != -9999){
                    minTemp = currentRow;
                }
            }
         return minTemp;
    }
    
    public void coldestHourInFileTester(){
        //this method gives me the lowest temperature of a day for a selected file, by printing it in a readable format
        FileResource fr = new FileResource();
        CSVRecord lowest = coldestHourInFile(fr.getCSVParser());
        System.out.println("coldest temp is " + lowest.get("TemperatureF") + " at ");
    }
    
    
    public String fileWithColdestTemperature() {
        //this method takes the coldest temp. by the hour in many selected files and returns a string with the coldest temperature
        CSVRecord lowestSoFar = null;
        DirectoryResource d = new DirectoryResource();
        for ( File f : d.selectedFiles()){
            FileResource fr = new FileResource(f);
            CSVRecord current = coldestHourInFile(fr.getCSVParser());
            lowestSoFar = lowestOfTwo(current, lowestSoFar);
        }
        String result = "this is the coldest temp of the period: " + lowestSoFar.get("TemperatureF")+ " in file "+ lowestSoFar.get("DateUTC").substring(0,10)+".csv and the date " + lowestSoFar.get("DateUTC");
        System.out.println(result);
        return result;
    }
    
    public CSVRecord lowestHumidityInFile(CSVParser parser){
        CSVRecord minHum = null; //null is really important when iterating CSVRecord files to do comparisons. If I try 0, I will get an error as it is a csvrecord variable type, not an int or double.
         for (CSVRecord currentRow : parser){
           minHum = lowestOfTwoHum(currentRow, minHum);
        }
        return minHum;
    }
    
    public CSVRecord lowestOfTwoHum(CSVRecord currentRow,CSVRecord minHum){
        //compares two humidities in csvrecords and gives us the lowest value  
        if (minHum == null) {
                minHum = currentRow;
         }
         else{
             if (!currentRow.get("Humidity").equals("N/A")){
                 //there are n/a values and we want to ignore them
             double currentHum = Double.parseDouble(currentRow.get("Humidity"));
             double minHumNum = Double.parseDouble(minHum.get("Humidity"));
                if (currentHum < minHumNum){
                    minHum = currentRow;
                }
            }
         }
         return minHum;
    }

    
    public void testLowestHumidityInFile(){
        //this method gives me the lowest humidity value of a day for a selected file, by printing it in a readable format
        FileResource fr = new FileResource();
        CSVRecord lowest =  lowestHumidityInFile(fr.getCSVParser());
        System.out.println("lowest humidity is " + lowest.get("Humidity") + " at "+  lowest.get("DateUTC"));
    }
    
    public void lowestHumidityInManyFiles(){
        //Takes several files and gives you the lowest humidity
        CSVRecord lowestSoFar = null;
        DirectoryResource d = new DirectoryResource();
        for ( File f : d.selectedFiles()){
            FileResource fr = new FileResource(f);
            CSVRecord current = lowestHumidityInFile(fr.getCSVParser());
            // System.out.println(current); to check that is getting the minimum of every file
            lowestSoFar = lowestOfTwoHum(current, lowestSoFar);
        }
        String result = "this is the lowest humidity of the period: " + lowestSoFar.get("Humidity")+ " in file "+ lowestSoFar.get("DateUTC");
        System.out.println(result);
    }
    
    public double averageTemperatureInFile(CSVParser parser){
        //Gets the average of every temperature of a day
        double averageTemp = 0;
        double count = 0;
        for (CSVRecord temp : parser){
            double tempNum = Double.parseDouble(temp.get("TemperatureF"));
            averageTemp = averageTemp + tempNum;
            count = count +1;
        }
        return averageTemp/count;
    }
    
    public void testaverageTemperatureInFile(){
        //this method gives me the lowest humidity value of a day for a selected file, by printing it in a readable format
        FileResource fr = new FileResource();
        CSVParser parser = fr.getCSVParser();
        System.out.println("Average temperature is: " +averageTemperatureInFile(parser));
        System.out.println("lowest humidity is " + lowest.get("Humidity") + " at "+  lowest.get("DateUTC"));
    }
}
