
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace project1
{
    public partial class Employee : Form
    {
        public Employee()
        {
            InitializeComponent();
        }

        private void Employee_Load(object sender, EventArgs e)
        {
            listView1.Items.Clear();
            List<Employee1> employeeList;
            try
            {
                employeeList = Employee2.GetEmployee1();
                if (employeeList.Count > 0)
                {
                    Employee1 employee;
                    for (int i=0;i<employeeList.Count; i++)
                    {
                        employee = employeeList[i];
                        listView1.Items.Add(employee.EmployeeNumber.ToString());
                        listView1.Items[i].SubItems.Add(employee.FirstName);
                        listView1.Items[i].SubItems.Add(employee.LastName);
                        listView1.Items[i].SubItems.Add(employee.Phone);
                        listView1.Items[i].SubItems.Add(employee.Age);
                        listView1.Items[i].SubItems.Add(employee.Address);
                    }
                }
                else { MessageBox.Show("There are no Employees. ", "Alert"); }
            }
            catch(Exception ex){ MessageBox.Show(ex.Message, ex.GetType().ToString()); }
        }

        private void sumbit_Click(object sender, EventArgs e)
        {
            Employee2.AddEmployee1(txtEFirstName.Text,txtELastName.Text,txtEPhone.Text,txtEAge.Text,txtEAddress.Text);
            txtEFirstName.Text = "";
            txtELastName.Text = "";
            txtEPhone.Text = "";
            txtEAge.Text = "";
            txtEAddress.Text = "";
            this.Employee_Load(this, null);

        }
    }
}
