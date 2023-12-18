<template>
    <div>
      <div class="container mt-5">
        <div class="card">
          <div class="card-header">
            <h4>Loan Application</h4>
          </div>
          <div class="card-body tab-content">
            <!-- Personal Info Tab -->
            
              <div class="mb-3">
                <label for="FirstName">First Name</label>
                <input type="text" id="FirstName" v-model="loan.FirstName" class="form-control" required />
              </div>
              <div class="mb-3">
                <label for="LastName">Last Name</label>
                <input type="text" id="LastName" v-model="loan.LastName" class="form-control" required />
              </div>
           
  
            <!-- Contact Info Tab -->
            
              <div class="mb-3">
                <label for="Email">Email</label>
                <input type="email" id="Email" v-model="loan.Email" class="form-control" required />
              </div>
              <div class="mb-3">
                <label for="NIN">National Insurance Number (NIN)</label>
                <input type="text" id="NIN" v-model="loan.NIN" class="form-control" required />
              </div>
              <div class="mb-3">
                <label for="Birthdate">Birthdate</label>
                <input type="date" id="Birthdate" v-model="loan.Birthdate" class="form-control" required />
              </div>
            
  
            <!-- ID Card Tab -->
            
              <div class="mb-3">
                <label for="IdCardType">ID Card Type</label>
                <select id="IdCardType" v-model="loan.IdCardType" class="form-control" required>
                  <option value="DriverLicense">Driver License</option>
                  <option value="StateId">State ID</option>
                  <option value="Other">Other</option>
                </select>
              </div>
              <div class="mb-3">
                <label for="IdCardNumber">ID Card Number</label>
                <input type="text" id="IdCardNumber" v-model="loan.IdCardNumber" class="form-control" required />
              </div>
              <div class="mb-3">
                <label for="IdCardOrigin">ID Card Origin</label>
                <input type="text" id="IdCardOrigin" v-model="loan.IdCardOrigin" class="form-control" required />
              </div>
           
  
            <!-- Income Tab -->
            
              <div class="mb-3">
                <label for="IncType">Income Type</label>
                <select id="IncType" v-model="loan.IncType" class="form-control" required>
                  <option value="RegularJob">Regular Job</option>
                  <option value="SelfEmployed">Self-Employed</option>
                  <option value="SocialSecurity">Social Security</option>
                </select>
              </div>
              <div class="mb-3">
                <label for="IncomeName">Income Name</label>
                <input type="text" id="IncomeName" v-model="loan.IncomeName" class="form-control" required />
              </div>
              <div class="mb-3">
                <label for="JobTitle">Job Title</label>
                <input type="text" id="JobTitle" v-model="loan.JobTitle" class="form-control" required />
              </div>
              <div class="mb-3">
                <label for="Department">Department</label>
                <input type="text" id="Department" v-model="loan.Department" class="form-control" required />
              </div>
              <div class="mb-3">
                <label for="IncomeStartDate">Income Start Date</label>
                <input type="date" id="IncomeStartDate" v-model="loan.IncomeStartDate" class="form-control" required />
              </div>
            
  
            <!-- Bank Account Tab -->
            
              <div class="mb-3">
                <label for="AccountType">Account Type</label>
                <select id="AccountType" v-model="loan.AccountType" class="form-control" required>
                  <option value="Checking">Checking</option>
                  <option value="Savings">Savings</option>
                </select>
              </div>
              <div class="mb-3">
                <label for="RoutingNumber">Routing Number</label>
                <input type="text" id="RoutingNumber" v-model="loan.RoutingNumber" class="form-control" required />
              </div>
              <div class="mb-3">
                <label for="AccountNumber">Account Number</label>
                <input type="text" id="AccountNumber" v-model="loan.AccountNumber" class="form-control" required />
              </div>
              <div class="mb-3">
                <label for="BankName">Bank Name</label>
                <input type="text" id="BankName" v-model="loan.BankName" class="form-control" required />
              </div>
              <div class="mb-3">
                <label for="IsDirectDepositBank">Is Direct Deposit Bank?</label>
                <input type="checkbox" id="IsDirectDepositBank" v-model="loan.IsDirectDepositBank" />
              </div>
              <div class="mb-3">
                <label for="RequestedAmount">Requested Amount</label>
                <input type="number" id="RequestedAmount" v-model="loan.RequestedAmount" class="form-control" required />
              </div>

            <button type="submit" @click="saveLoan" class="btn btn-primary">Submit</button>
          </div>
        </div>
      </div>

      
    </div>
  </template>
  
  
  <script>
  export default {
    data() {
        return {
            loan: {
                FirstName: '',
                LastName: '',
                Addr1: '',
                Addr2: '',
                City: '',
                State: '',
                PostalCode: '',
                MonthsAt: null,
                MonthlyPayment: null,
                Email: '',
                NIN: '',
                Birthdate: null,
                PhoneType: 'Home',
                Number: '',
                IdCardType: 'DriverLicense',
                IdCardNumber: '',
                IdCardOrigin: '',
                IncType: 'RegularJob',
                IncomeName: '',
                JobTitle: '',
                Department: '',
                IncomeStartDate: null,
                PayAmount: null,
                LastPayDate: null,
                NextPayDate: null,
                PayFrequency: 'Monthly',
                IsDirectDeposit: false,
                AccountType: 'Checking',
                RoutingNumber: '',
                AccountNumber: '',
                BankName: '',
                IsDirectDepositBank: false,
                RequestedAmount: null,
            
            },
        };
    },

    methods: {
     
        saveLoan(){

            axios.post('http://127.0.0.1:8000/api/loans', this.loan)
            .then(res => {

                console.log(res);
                alert(res.data.message);

                this.loan = {
                    FirstName: '',
                    LastName: '',
                    Addr1: '',
                    Addr2: '',
                    City: '',
                    State: '',
                    PostalCode: '',
                    MonthsAt: null,
                    MonthlyPayment: null,
                    Email: '',
                    NIN: '',
                    Birthdate: null,
                    PhoneType: 'Home',
                    Number: '',
                    IdCardType: 'DriverLicense',
                    IdCardNumber: '',
                    IdCardOrigin: '',
                    IncType: 'RegularJob',
                    IncomeName: '',
                    JobTitle: '',
                    Department: '',
                    IncomeStartDate: null,
                    PayAmount: null,
                    LastPayDate: null,
                    NextPayDate: null,
                    PayFrequency: 'Monthly',
                    IsDirectDeposit: false,
                    AccountType: 'Checking',
                    RoutingNumber: '',
                    AccountNumber: '',
                    BankName: '',
                    IsDirectDepositBank: false,
                    RequestedAmount: null,
                }

            })
            .catch(error => {
            // Handle error here (e.g., show an error message)
            console.error('Error submitting form:', error);
            });
        }

    },
  };
  </script>
  
  <style scoped>
  /* Add your custom styles here if needed */
  </style>
  