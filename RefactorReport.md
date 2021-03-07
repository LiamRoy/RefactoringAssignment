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



## Explaining Variables:

## Why use the Explaining Variables:
   - An explanatory variable is a type of independent variable.
   - The two terms are often used interchangeably. But there is a subtle difference between the two. 
   - When a variable is independent, it is not affected at all by any other variables. When a variable isn’t independent for certain, it’s an explanatory variable.
   - I implemented it as it helps to read code better. IF statements can become clustered and are hard to follow so implementing these variables make them more understandable.

 ## Code before the Explaining Variables implemented:
 
  # AddRecordDialog.java
   ### Before:
   
    public boolean checkInput() {
		boolean valid = true;
		// if any of inputs are in wrong format, colour text field and display message
		if (ppsField.getText().equals("")) {
			ppsField.setBackground(new Color(255, 150, 150));
			valid = false;
		}// end if
		if (this.parent.correctPps(this.ppsField.getText().trim(), -1)) {
			ppsField.setBackground(new Color(255, 150, 150));
			valid = false;
		}// end if
		if (surnameField.getText().isEmpty()) {
			surnameField.setBackground(new Color(255, 150, 150));
			valid = false;
		}// end if
		if (firstNameField.getText().isEmpty()) {
			firstNameField.setBackground(new Color(255, 150, 150));
			valid = false;
		}// end if
		if (genderCombo.getSelectedIndex() == 0) {
			genderCombo.setBackground(new Color(255, 150, 150));
			valid = false;
		}// end if
		if (departmentCombo.getSelectedIndex() == 0) {
			departmentCombo.setBackground(new Color(255, 150, 150));
			valid = false;
		}// end if
		try {// try to get values from text field
			Double.parseDouble(salaryField.getText());
			// check if salary is greater than 0
			if (Double.parseDouble(salaryField.getText()) < 0) {
				salaryField.setBackground(new Color(255, 150, 150));
				valid = false;
			}// end if
		}// end try
		catch (NumberFormatException num) {
			salaryField.setBackground(new Color(255, 150, 150));
			valid = false;
		}// end catch
		if (fullTimeCombo.getSelectedIndex() == 0) {
			fullTimeCombo.setBackground(new Color(255, 150, 150));
			valid = false;
		}// end if
		return valid;
	}// end checkInput

	
 ### After:
 
 	public boolean checkInput() {
		boolean valid = true;
		final boolean ppsFieldEquals, parentCorrectPps,surnameFieldEmpty,firstNameFieldEmpty, genderCombo0, departmentCombo0,
		salaryFieldGreaterThan0, fullTimeCombo0;
		ppsFieldEquals = (ppsField.getText().equals(""));
		parentCorrectPps = (this.parent.correctPPS(this.ppsField.getText().trim(), -1));
		surnameFieldEmpty = (surnameField.getText().isEmpty());
		firstNameFieldEmpty = (firstNameField.getText().isEmpty());
		genderCombo0 = (genderCombo.getSelectedIndex() == 0);
		departmentCombo0 = (departmentCombo.getSelectedIndex() == 0);
		salaryFieldGreaterThan0 = (Double.parseDouble(salaryField.getText()) < 0);
		fullTimeCombo0 = (fullTimeCombo.getSelectedIndex() == 0);
		
		// if any of inputs are in wrong format, colour text field and display message
		if (ppsFieldEquals) {
			ppsField.setBackground(new Color(255, 150, 150));
			valid = false;
		}// end if
		if (parentCorrectPps) {
			ppsField.setBackground(new Color(255, 150, 150));
			valid = false;
		}// end if
		if (surnameFieldEmpty) {
			surnameField.setBackground(new Color(255, 150, 150));
			valid = false;
		}// end if
		if (firstNameFieldEmpty) {
			firstNameField.setBackground(new Color(255, 150, 150));
			valid = false;
		}// end if
		if (genderCombo0) {
			genderCombo.setBackground(new Color(255, 150, 150));
			valid = false;
		}// end if
		if (departmentCombo0) {
			departmentCombo.setBackground(new Color(255, 150, 150));
			valid = false;
		}// end if
		try {// try to get values from text field
			Double.parseDouble(salaryField.getText());
			// check if salary is greater than 0
			if (salaryFieldGreaterThan0) {
				salaryField.setBackground(new Color(255, 150, 150));
				valid = false;
			}// end if
		}// end try
		catch (NumberFormatException num) {
			salaryField.setBackground(new Color(255, 150, 150));
			valid = false;
		}// end catch
		if (fullTimeCombo0) {
			fullTimeCombo.setBackground(new Color(255, 150, 150));
			valid = false;
		}// end if
		return valid;
	}// end checkInput

