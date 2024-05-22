# SI_2024_lab2_223160

1. public class SILab2 {
    public static boolean checkCart(List<Item> allItems, int payment){  //1
        if (allItems == null){ //1
            throw new RuntimeException("allItems list can't be null!"); //2
        }

        float sum = 0; //3

        for (int i = 0; i < allItems.size(); i++){ //4.1 4.2 4.3
            Item item = allItems.get(i);  //5
            if (item.getName() == null || item.getName().length() == 0){  //6
                item.setName("unknown");  //7
            }
            if (item.getBarcode() != null){  //8
                String allowed = "0123456789";   //9
                char chars[] = item.getBarcode().toCharArray();  
                for (int j = 0; j < item.getBarcode().length(); j++){  //10.1 10.2 10.3
                    char c = item.getBarcode().charAt(j);  //11
                    if (allowed.indexOf(c) == -1){  //12
                        throw new RuntimeException("Invalid character in item barcode!");  //13
                    }
                }
                if (item.getDiscount() > 0){ //14
                    sum += item.getPrice()*item.getDiscount();  //15
                } 
                else {
                    sum += item.getPrice();  //16
                }
            }   // 17
            else {
                throw new RuntimeException("No barcode!");  //18
            }
            if (item.getPrice() > 300 && item.getDiscount() > 0 && item.getBarcode().charAt(0) == '0'){  //19
                sum -= 30;  //20
            }
        }   
        if (sum <= payment){  //21
            return true;  //22
        }
        else {
            return false;  //23
        }
    }  //24
}

2. ![Control Flow Graph](https://github.com/donaivanova/SI_2024_lab2_223160/assets/165796806/7bc5a671-df20-4337-86a0-e37a6f36572e)
   
3. Цикломатската комплексност на овој код е 10 затоа што има 10 региони, а исто така бројот на ребра е 36, бројот на јазли е 28, па според формулата 36-28+2=10 што дава иста вредност за цикломатската комплексност.

4. ![image](https://github.com/donaivanova/SI_2024_lab2_223160/assets/165796806/4eda0fcc-14bd-454c-9e75-8a432ef76b41)
![image](https://github.com/donaivanova/SI_2024_lab2_223160/assets/165796806/4cc4da74-4ce7-46c6-985f-571aeb1dcaf2)


5. ![image](https://github.com/donaivanova/SI_2024_lab2_223160/assets/165796806/17667d18-d4d6-4e2e-a90a-9e0ec956cc53)

