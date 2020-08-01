<template>
    <Page>
        <ActionBar title="Digital Tech Demo"/>
        <StackLayout margin="12px">
          <Label text="Add Employee" fontWeight="bold" fontSize="30"/>
          <Label text="Employee" fontSize="14"/>
          <TextField v-model="employee.name" hint="Enter employee name..."/>
          <Label text="Employee Email" fontSize="14"/>
          <TextField v-model="employee.email" hint="Enter employee email address..."/>
          <Button @tap="addEmployee" text="Add Employee" backgroundColor="#43b883"/>

          <StackLayout>
            <Label text="Employees" fontWeight="bold" fontSize="30" margin="12px"/>
            <ListView for="person in employees">
              <v-template>
                <!-- Shows the list item label in the default color and style. -->
                <StackLayout>
                  <Label :text="person.name" fontSize="17"/>
                  <Label :text="person.email" fontSize="14"/>
                </StackLayout>
              </v-template>
            </ListView>
          </StackLayout>
        </StackLayout>
    </Page>
</template>

<script>
  export default {
    data() {
      return {
        employee: {
            name : '',
            email: '',
        },
        employees: [
          {
            id: 1,
            name: 'Richard Hendricks',
            email: 'richard@piedpiper.com',
          },
          {
            id: 2,
            name: 'Bertram Gilfoyle',
            email: 'gilfoyle@piedpiper.com',
          },
          {
            id: 3,
            name: 'Dinesh Chugtai',
            email: 'dinesh@piedpiper.com',
          },
        ],
      }
    },
    methods: {
      addEmployee: function(){
        const lastId = this.employees.length > 0 ? this.employees[this.employees.length - 1].id : 0;
        const id = lastId + 1;
        const newEmployee = { ...this.employee, id };

        this.employees = [...this.employees, newEmployee]

        this.employee.name = ''
        this.employee.email = ''
      }
    },
  }
</script>

<style scoped>
    ActionBar {
        background-color: #53ba82;
        color: #ffffff;
    }

    .message {
        vertical-align: center;
        text-align: center;
        font-size: 20;
        color: #333333;
    }

    .addEmployeeButton{
        font-weight: bold;
    }
</style>
