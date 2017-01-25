# expense
expenses for car
               



                   System.out.print(
				"arr0 = Enter oil(in format 000,000 = 000000 or 12,34 = 12340);\n"+
				"arr1 = 1-nothing; 2-winter; 3-klimatic;\n" +
				"arr2 = Enter expense(don't use comma); \n"+
				" \t \t ZAFIRA  (gaz - 11.44 lit;      petrol- 10.55)\n"+
				" \t \t PEUGEOT (gaz - 11.13 lit;      petrol- 10.10)\n"+
		        " \t \t W-BORA  (gaz - 11.73 lit;      petrol- 10.18)\n"+
				"arr3 = Input km v Sofiq (36)\n"+
				"arr4 = Input km do Sofiq (168)\n"+
				"Enter number with space = \n");
		    
		   BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		   int arr[] = new int[5];
		   String line = null;
				try {
					line = br.readLine();
				} catch (IOException e) {
					e.printStackTrace();
				} 
				String[] strs = line.trim().split("\\s+");
		   for (int i = 0; i < 5; i++) {
			  arr[i] = Integer.parseInt(strs[i]);
				}
				
		   float arO = arr[0];	
	       float oilExpense = arO/1000;
	       float oil = 0;
	       int option = nextInt(arr[1]);
	          if (option == 3) {
		     oil = (float) (oilExpense/1.25);
	       }  if (option == 2) {
		       oil = (float) (oilExpense/1.05);
	       }  if (option == 1) {
		        oil = oilExpense;
	       }
	       
	       float expense = expenses(arr[2]);
	       int kmVSofiq = arr[3];
	       int kmDoSofiq = arr[4];
	       int doIvSofiq = kmVSofiq + kmDoSofiq;
	       float city = (expense/100) + (3*(expense/100)/100);	
	       float sofia =   (kmDoSofiq*expense/100) + ((kmVSofiq*expense/100) + 
	    		   (kmVSofiq*expense/100)*25/100);
	       float allSofia = oil/sofia;
	       int clearSofia = (int) Math.floor(allSofia);
	        System.out.println("_____________________________________________");
	        System.out.println(clearSofia + " курса София");
	       float litrySofia =  clearSofia*sofia;
	       float litryCity = oil - litrySofia;
	       float kmCity = litryCity/city;
	       int clearKmCity = (int) Math.ceil(kmCity);
	       if (clearKmCity % 2 != 0)
		      clearKmCity= clearKmCity + 1;
	       float allkm = clearSofia*doIvSofiq + clearKmCity;
	       float alllitry1 = Math.round((allkm*expense/100)*1000);
	       float alllitry = alllitry1/1000;      // закръгляваме Math.round(а * 1000)/1000
	        System.out.println("Общо км = " + allkm +" км , литри(кг) = "+alllitry);
	       float dobavkaCity1 = Math.round(((clearKmCity*expense/100 + (3*clearKmCity*expense/100)/100)
	    		   -clearKmCity*expense/100)*1000);
	       float dobavkaCity = dobavkaCity1/1000;      // закръгляваме Math.round(а * 1000)/1000
	        System.out.println("Градско "+clearKmCity +" km,  +3% = + "+ dobavkaCity +" l(kg)"); 
	       float kmInSofia = kmVSofiq*clearSofia;
	       float dobavkaSofia1 =Math.round(((kmInSofia*expense/100 + (25*kmInSofia*expense/100)/100)
	    		   - kmInSofia*expense/100)*1000);
	       float dobavkaSofia = dobavkaSofia1/1000;    // закръгляваме Math.round(а * 1000)/1000
	        System.out.println("София " + kmInSofia+" км, +25% = + "+dobavkaSofia + " l(kg)");
	       float winter1 = Math.round((((alllitry + dobavkaCity + dobavkaSofia) +
	    		   5*(alllitry + dobavkaCity + dobavkaSofia)/100 ) - 
	    		   (alllitry + dobavkaCity + dobavkaSofia))*1000);
	       float winter = winter1/1000;      // закръгляваме Math.round(а * 1000)/1000
	       float klimatic1 =Math.round((((alllitry + dobavkaCity + dobavkaSofia) + 
	    		   25*(alllitry + dobavkaCity + dobavkaSofia)/100 ) - 
	    		   (alllitry + dobavkaCity + dobavkaSofia))*1000); 
	       float klimatic = klimatic1/1000;   // закръгляваме Math.round(а * 1000)/1000
	        if (option == 1) {
	    	    klimatic = 0;
	    	    winter = 0;
	        }
	        if (option == 2) {
	    	    klimatic = 0;
	       }
	        if (option == 3) {
	    	    winter = 0;
	       }
	        System.out.println("Зимни + 5% = + " + winter);
	        System.out.println("Климатик + 25% = + " + klimatic);
	       float litry1 = Math.round((alllitry + dobavkaCity +dobavkaSofia + winter + klimatic)*1000);
	       float litry = litry1/1000;        // закръгляваме Math.round(а * 1000)/1000
		    System.out.println("Общо " +litry+ " литри(кг), Заредени "+ oilExpense +" литри(кг)");
	   
	}

	   private static int nextInt(int n) {
		   int option = n;
		   while (option < 1 || option > 3) {
	       System.out.println("Wrong option! arr1");break;
	       }
		   return option;
	       }

	   private static float expenses(float n) {
	     float expense  = n/100;
	     ArrayList<Float> expenses = new ArrayList<Float>();
	          expenses.add((float) 11.44);
	          expenses.add((float) 10.55);
	          expenses.add((float) 11.13);
	          expenses.add((float) 10.10);
	          expenses.add((float) 11.73);
	          expenses.add((float) 10.18);
	     while (!expenses.contains(expense) ) {
	       System.out.print("Wrong expence! arr2 ");break;
	     }
	     return expense;
	     
	}
}



