# RefactoringAssignment

### Refactoring Report:

- Strategy Pattern implemented
- Explaining Variables added in if statement methods


## Strategy Pattern:

## Why use the Strategy Pattern:
  - The Strategy pattern lets you isolate the code, internal data, and dependencies of various algorithms from the rest of the code.
  - The Strategy pattern is a common pattern which can be implemented in many occasions. 
  - I believe using the Strategy pattern helps to make code clearer and easier to understand. This is why i implemented it.
  ## Code before the Strategy pattern implemented:
  
  # EmployeeDetails.java
   ### Before:
      public boolean correctPps(String pps, long currentByte) {
		boolean ppsExist = false;
		// check for correct PPS format based on assignment description
		if (pps.length() == 8 || pps.length() == 9) {
			if (Character.isDigit(pps.charAt(0)) && Character.isDigit(pps.charAt(1))
					&& Character.isDigit(pps.charAt(2))	&& Character.isDigit(pps.charAt(3)) 
					&& Character.isDigit(pps.charAt(4))	&& Character.isDigit(pps.charAt(5)) 
					&& Character.isDigit(pps.charAt(6))	&& Character.isLetter(pps.charAt(7))
					&& (pps.length() == 8 || Character.isLetter(pps.charAt(8)))) {
				// open file for reading
				application.openReadFile(file.getAbsolutePath());
				// look in file is PPS already in use
				ppsExist = application.isPpsExist(pps, currentByte);
				application.closeReadFile();// close file for reading
			} // end if
			else
				ppsExist = true;
		} // end if
		else
			ppsExist = true;

		return ppsExist;
	}// end correctPPS
	
   ### After:
   	###	EmployeeDetails.java	###
	
	public Boolean correctPPS(String pps, long currentByte) {
		ppsType = new correctPPS();
		// open file for reading
		application.openReadFile(file.getAbsolutePath());
		// look in file is PPS already in use
		//ppsExist = application.isPpsExist(pps, currentByte);
		application.closeReadFile();// close file for reading
		return ppsType.correctPPS(pps, currentByte);
	}
	
	###	PPSInterface.java	###
	
	public interface PPSInterface {

	Boolean correctPPS(String pps, long currentByte);
	
	}

	###	correctPPS.java	###
	
	public class correctPPS implements PPSInterface{
	
	Employee employee = new Employee();

	@Override
	public Boolean correctPPS(String pps, long currentByte) {
		boolean ppsExist = false;
		// check for correct PPS format based on assignment description
		if (pps.length() == 8 || pps.length() == 9) {
			if (Character.isDigit(pps.charAt(0)) && Character.isDigit(pps.charAt(1))
					&& Character.isDigit(pps.charAt(2))	&& Character.isDigit(pps.charAt(3)) 
					&& Character.isDigit(pps.charAt(4))	&& Character.isDigit(pps.charAt(5)) 
					&& Character.isDigit(pps.charAt(6))	&& Character.isLetter(pps.charAt(7))
					&& (pps.length() == 8 || Character.isLetter(pps.charAt(8)))) {
				
			} // end if
			else
				ppsExist = true;
		} // end if
		else
			ppsExist = true;

		return ppsExist;
	}// end correctPPS

	}
