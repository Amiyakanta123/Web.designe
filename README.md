# Web.designe
from tkinter import*
from tkinter import ttk
from PIL import Image, ImageTk
import mysql.connector
from tkinter import messagebox

class Employee:
    def __init__(self,root):
        self.root=root
        self.root.geometry("1530x790+0+0")
        self.root.title('Employee Management System')

        #Variable
        self.var_dep=StringVar()
        self.var_name=StringVar()
        self.var_designition=StringVar()
        self.var_email=StringVar()
        self.var_address=StringVar()
        self.var_married=StringVar()
        self.var_dob=StringVar()
        self.var_doj=StringVar()
        self.var_idproofcomb=StringVar()
        self.var_idproof=StringVar()
        self.var_gender=StringVar()
        self.var_phone=StringVar()
        self.var_salary=StringVar()
        self.var_country=StringVar()
        

        lbl_title=Label(self.root,text='EMPLOYEE MANAGEMENT SYSTEM',font=('times new roman',37,'bold'),fg='darkblue',bg='white')
        lbl_title.place(x=0,y=0,width=1530,height=50)


        #logos
        img_logo=Image.open('college_Image/images.png')
        img_logo=img_logo.resize((50,50),Image.LANCZOS)
        self.photo_logo=ImageTk.PhotoImage(img_logo)

        self.logo=Label(self.root,image=self.photo_logo)
        self.logo.place(x=270,y=0,width=40,height=40)

        # Image Frame
        img_frame=Frame(self.root,bd=2,relief=RIDGE,bg='white')
        img_frame.place(x=0,y=50,width=1530,height=160)

         #1st 
        img1=Image.open('college_Image//images.jpeg')
        img1=img1.resize((540,160),Image.LANCZOS)
        self.photo1=ImageTk.PhotoImage(img1)

        self.img1=Label(img_frame,image=self.photo1)
        self.img1.place(x=0,y=0,width=540,height=160)

        #2nd
        img_2=Image.open('college_Image//download (1).jpeg')
        img_2=img_2.resize((540,160),Image.LANCZOS)
        self.photo2=ImageTk.PhotoImage(img_2)

        self.img_2=Label(img_frame,image=self.photo2)
        self.img_2.place(x=540,y=0,width=540,height=160)


         #3rd
        img3=Image.open('college_Image//download.jpeg')
        img3=img3.resize((540,160),Image.LANCZOS)
        self.photo3=ImageTk.PhotoImage(img3)

        self.img3=Label(img_frame,image=self.photo3)
        self.img3.place(x=1000,y=0,width=540,height=160)

         #Main Frame
        Main_frame=Frame(self.root,bd=2,relief=RIDGE,bg='white')
        Main_frame.place(x=10,y=220,width=1500,height=560)

         #Upper Frame
        upper_frame=LabelFrame(Main_frame,bd=2,relief=RIDGE,bg='white',text='Employee Information',font=('times new roman',12,'bold'),fg='darkblue')
        upper_frame.place(x=10,y=10,width=1480,height=270)

         #Lables and Entery fields
        lbl_dep=Label(upper_frame,text='Department',font=('arial',11,'bold'),bg='white')
        lbl_dep.grid(row=0,column=0,padx=2,sticky=W)

        combo_dep=ttk.Combobox(upper_frame,textvariable=self.var_dep,font=('arial',11,'bold'),width=17,state='readonly')
        combo_dep['value']=('Select Department','HR','Software Engineer','Manager','Finance','Manufacture','Resource and dev')
        combo_dep.current(0)
        combo_dep.grid(row=0,column=1,padx=2,pady=10,sticky=W)
         

          #Name
        lbl_Name=Label(upper_frame,text='Name:',font=('arial',11,'bold'),bg='white')
        lbl_Name.grid(row=0,column=2,padx=2,pady=7,sticky=W)

        txt_name=ttk.Entry(upper_frame,textvariable=self.var_name,width=22,font=("arial",11,"bold"))
        txt_name.grid(row=0,column=3,padx=2,pady=7)

        #lbl_Designition
        lbl_Designition=Label(upper_frame,text='Designition:',font=('arial',11,'bold'),bg='white')
        lbl_Designition.grid(row=1,column=0,padx=2,pady=7,sticky=W)

        txt_Designition=ttk.Entry(upper_frame,textvariable=self.var_designition,width=22,font=("arial",11,"bold"))
        txt_Designition.grid(row=1,column=1,sticky=W,padx=2,pady=7)

        #lbl_Email
        lbl_Email=Label(upper_frame,text='Email_Id:',bg='white',font=("arial",12,"bold"))
        lbl_Email.grid(row=1,column=2,padx=2,pady=7,sticky=W)

        txt_Email=ttk.Entry(upper_frame,textvariable=self.var_email,width=22,font=("arial",11,"bold"))
        txt_Email.grid(row=1,column=3,padx=2,pady=7)

        #Address
        lbl_Address=Label(upper_frame,font=("arial",11,"bold"),text='Address:',bg='white')
        lbl_Address.grid(column=0,row=2,padx=2,pady=7,sticky=W)

        txt_Address=ttk.Entry(upper_frame,textvariable=self.var_address,width=22,font=("arial",11,"bold"))
        txt_Address.grid(row=2,column=1,padx=2,pady=7)


        #Married
        lbl_Married=Label(upper_frame,text='Married:',bg='white',font=("arial",11,"bold"))
        lbl_Married.grid(row=2,column=2,padx=2,pady=7,sticky=W)

        com_txt_Married=ttk.Combobox(upper_frame,textvariable=self.var_married,state='readonly',width=18,font=("arial",11,"bold"))
        com_txt_Married['value']=('Married','Unmarried')
        com_txt_Married.current(0)
        com_txt_Married.grid(row=2,column=3,padx=2,pady=7,sticky=W)
        

        #DOB
        lbl_DOB=Label(upper_frame,text='DOB:',bg='white',font=("arial",11,"bold"))
        lbl_DOB.grid(row=3,column=0,padx=2,pady=7,sticky=W)

        txt_DOB=ttk.Entry(upper_frame,textvariable=self.var_dob,width=22,font=("arial",11,"bold"))
        txt_DOB.grid(row=3,column=1,padx=2,pady=7)

        #DOJ
        lbl_DOJ=Label(upper_frame,text='DOJ:',bg='white',font=("arial",11,"bold"))
        lbl_DOJ.grid(row=3,column=2,padx=2,pady=7,sticky=W)

        txt_DOj=ttk.Entry(upper_frame,textvariable=self.var_doj,width=22,font=("arial",11,"bold"))
        txt_DOj.grid(row=3,column=3,padx=2,pady=7)

        #Id proof
        com_txt_proof=ttk.Combobox(upper_frame,state='readonly',width=17,font=("arial",11,"bold"))
        com_txt_proof['value']=('Select ID Proof','PAN CARD','ADHAR CARD','DRIVING LICENCE')
        com_txt_proof.current(0)
        com_txt_proof.grid(row=4,column=0,padx=2,pady=7,sticky=W)
        
        com_txt_proof=ttk.Entry(upper_frame,textvariable=self.var_idproof,width=22,font=("arial",11,"bold"))
        com_txt_proof.grid(row=4,column=1,padx=2,pady=7)

        #Gender
        lbl_Gender=Label(upper_frame,text='Gender:',bg='white',font=("arial",11,"bold"))
        lbl_Gender.grid(row=4,column=2,padx=2,pady=7,sticky=W)

        com_txt_Gender=ttk.Combobox(upper_frame,textvariable=self.var_gender,state='readonly',width=18,font=("arial",11,"bold"))
        com_txt_Gender['value']=('Male','Female','Other')
        com_txt_Gender.current(0)
        com_txt_Gender.grid(row=4,column=3,padx=2,pady=7,sticky=W)


        #Phone
        lbl_Phone=Label(upper_frame,text='Phone No:',bg='white',font=("arial",11,"bold"))
        lbl_Phone.grid(row=0,column=4,padx=2,pady=7,sticky=W)

        txt_Phone=ttk.Entry(upper_frame,textvariable=self.var_phone,width=22,font=("arial",11,"bold"))
        txt_Phone.grid(row=0,column=5,padx=2,pady=7)

        #country
        lbl_country=Label(upper_frame,text='country:',bg='white',font=("arial",11,"bold"))
        lbl_country.grid(row=1,column=4,padx=2,pady=7,sticky=W)

        txt_country=ttk.Entry(upper_frame,textvariable=self.var_country
                              ,width=22,font=("arial",11,"bold"))
        txt_country.grid(row=1,column=5,padx=2,pady=7)

        #CTC
        lbl_CTC=Label(upper_frame,text='Salary(CTC):',bg='white',font=("arial",11,"bold"))
        lbl_CTC.grid(row=2,column=4,padx=2,pady=7,sticky=W)

        txt_CTC=ttk.Entry(upper_frame,textvariable=self.var_salary,width=22,font=("arial",11,"bold"))
        txt_CTC.grid(row=2,column=5,padx=2,pady=7)

         #Mask Image
        img_Mask=Image.open('college_Image\images_mask.jpeg')
        img_Mask=img_Mask.resize((220,220),Image.LANCZOS)
        self.photomask=ImageTk.PhotoImage(img_Mask)

        self.img_Mask=Label(upper_frame,image=self.photomask) 
        self.img_Mask.place(x=1000,y=0,width=220,height=220)

        #Button Frame
        button_frame=Frame(upper_frame,bd=2,relief=RIDGE,bg='white')
        button_frame.place(x=1290,y=10,width=170,height=210)

        #For add
        btn_add=Button(button_frame,text='Save',command=self.add_data,font=('arial',15,'bold'),width=13,bg='blue',fg='white')
        btn_add.grid(row=0,column=0,padx=1,pady=5)

        #For update
        btn_update=Button(button_frame,text='Update',font=('arial',15,'bold'),width=13,bg='blue',fg='white')
        btn_update.grid(row=1,column=0,padx=1,pady=5)

        #For delete
        btn_delete=Button(button_frame,text='Delete',command=self.delete_data,font=('arial',15,'bold'),width=13,bg='blue',fg='white')
        btn_delete.grid(row=2,column=0,padx=1,pady=5)

        #For clear
        btn_clear=Button(button_frame,text='Clear',font=('arial',15,'bold'),width=13,bg='blue',fg='white')
        btn_clear.grid(row=3,column=0,padx=1,pady=5)


        #down Frame
        lower_frame=LabelFrame(Main_frame,bd=2,relief=RIDGE,bg='white',text='Employee Information Table',font=('times new roman',12,'bold'),fg='darkblue')
        lower_frame.place(x=10,y=280,width=1480,height=270)

        #Search frame
        search_frame=LabelFrame(lower_frame,bd=2,relief=RIDGE,bg='white',text='Search Employee Information',font=('times new roman',12,'bold'),fg='darkblue')
        search_frame.place(x=0,y=0,width=1470,height=60)

        search_by=Label(search_frame,font=("arial",11,"bold"),text="Search By:",fg='white',bg='red')
        search_by.grid(row=0,column=0,sticky=W,padx=5)

        #Search
        
        com_txt_search=ttk.Combobox(search_frame,state='readonly',width=18,font=("arial",12,"bold"))
        com_txt_search['value']=('Select Option','Phone','id_proof')
        com_txt_search.current(0)
        com_txt_search.grid(row=0,column=1,padx=5,sticky=W)


        txt_search=ttk.Entry(search_frame,width=22,font=("arial",11,"bold"))
        txt_search.grid(row=0,column=2,padx=5)

        btn_search=Button(search_frame,text='Search',font=('arial',11,'bold'),width=14,bg='blue',fg='white')
        btn_search.grid(row=0,column=3,padx=5)

        btn_showAll=Button(search_frame,text='Show All',font=('arial',11,'bold'),width=14,bg='blue',fg='white')
        btn_showAll.grid(row=0,column=4,padx=5)

        stayhome=Label(search_frame,text='Wear a Mask',font=('times new roman',30,'bold'),bg='white',fg='red')
        stayhome.place(x=780,y=0,width=600,height=30)

        #Image
        img_logo_mask=Image.open('college_Image\images_mask(2).jpeg')
        img_logo_mask=img_logo_mask.resize((50,50),Image.LANCZOS)
        self.photoimg_logo_mask=ImageTk.PhotoImage(img_logo_mask)

        self.img_Mask=Label(search_frame,image=self.photoimg_logo_mask) 
        self.img_Mask.place(x=900,y=0,width=50,height=30)

        #Employee table
        #Table Frame
        table_frame=Frame(lower_frame,bd=3,relief=RIDGE)
        table_frame.place(x=0,y=60,width=1470,height=170)

        scroll_x=ttk.Scrollbar(table_frame,orient=HORIZONTAL)
        scroll_y=ttk.Scrollbar(table_frame,orient=VERTICAL)

        self.employee_table=ttk.Treeview(table_frame,column=('Dep','name','Degi','email','address','married','dob','doj','idproofcomb','idproof','gender','phone','country','salary'),xscrollcommand=scroll_x.set,yscrollcommand=scroll_y.set)

        scroll_x.pack(side=BOTTOM,fill=X)
        scroll_y.pack(side=RIGHT,fill=Y)

        scroll_x.config(command=self.employee_table.xview)
        scroll_y.config(command=self.employee_table.yview)

        self.employee_table.heading('Dep',text='Department')
        self.employee_table.heading('name',text='Name')
        self.employee_table.heading('Degi',text='Degignition')
        self.employee_table.heading('email',text='Email')
        self.employee_table.heading('address',text='Address')
        self.employee_table.heading('married',text='Married Status')
        self.employee_table.heading('dob',text='DOB')
        self.employee_table.heading('doj',text='DOJ')
        self.employee_table.heading('idproofcomb',text='ID Type')
        self.employee_table.heading('idproof',text='ID Proof')
        self.employee_table.heading('gender',text='Gender')
        self.employee_table.heading('phone',text='Phone')
        self.employee_table.heading('country',text='Country')
        self.employee_table.heading('salary',text='Salary')

        self.employee_table['show']='headings'

        self.employee_table.column('Dep',width=100)
        self.employee_table.column('name',width=100)
        self.employee_table.column('email',width=100)
        self.employee_table.column('address',width=100)
        self.employee_table.column('married',width=100)
        self.employee_table.column('dob',width=100)
        self.employee_table.column('doj',width=100)
        self.employee_table.column('idproofcomb',width=100)
        self.employee_table.column('idproof',width=100)
        self.employee_table.column('gender',width=100)
        self.employee_table.column('phone',width=100)
        self.employee_table.column('country',width=100)
        self.employee_table.column('salary',width=100)


        self.employee_table.pack(fill=BOTH,expand=2)
        self.employee_table.bind("<ButtonRelease>", self.get_cursor)

        self.fetch_data()

    
    #######Function Declarations#########
        



    def add_data(self):
        if self.var_dep.get()=="" or self.var_email.get()=="":
            messagebox.showerror('Error','All Fields are required')
        else:
            try:
                conn=mysql.connector.connect(host='localhost',username='root',password='AMIYA#84#gudu',database='first_proj')
                my_cursor=conn.cursor()                                                                                       
                my_cursor.execute('insert into employee1 values(%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s',(
                                                                                                                self.var_dep.get(),
                                                                                                                self.var_name.get(),
                                                                                                                self.var_designition.get(),
                                                                                                                self.var_email.get(),
                                                                                                                self.var_address.get(),
                                                                                                                self.var_married.get(),
                                                                                                                self.var_dob.get(),
                                                                                                                self.var_doj.get(),
                                                                                                                self.var_idproofcomb.get(),
                                                                                                                self.var_idproof.get(),
                                                                                                                self.var_gender.get(),
                                                                                                                self.var_phone.get(),
                                                                                                                self.var_salary.get(),
                                                                                                                self.var_country.get()
                                                                                                             ))
                conn.commit()
                self.fetch_data()
                conn.close()
                messagebox.showinfo('Success','Employee has been added',parent=self.root)
            except Exception as es:
                messagebox.showerror('Error',f'Due To:{str(es)}', parent=self.root)

    #fetch data
    def fetch_data(self):
        conn=mysql.connector.connect(host='localhost',username='root',password='AMIYA#84#gudu',database='first_proj')
        my_cursor=conn.cursor()
        my_cursor.execute('select * from employee1')
        data=my_cursor.fetchall()
        if len(data)!=0:
            self.employee_table.delete(*self.employee_table.get_children())
            for i in data:
                self.employee_table.insert("", END, values=i)
            conn.commit
        conn.close()

#Get Cursor
        
    def get_cursor(self, event=""):
        cursor_row=self.employee_table.focus()
        content=self.employee_table.item(cursor_row)
        data=content['values']

        self.var_dep.set(data[0]) 
        self.var_name.set(data[1]) 
        self.var_designition.set(data[2]) 
        self.var_email.set(data[3]) 
        self.var_address.set(data[4]) 
        self.var_married.set(data[5]) 
        self.var_dob.set(data[6]) 
        self.var_doj.set(data[7]) 
        self.var_idproofcomb.set(data[8]) 
        self.var_idproof.set(data[9])
        self.var_gender.set(data[10]) 
        self.var_phone.set(data[11])
        self.var_country.set(data[12])
        self.var_salary.set(data[13]) 


#for Update
    def update_data(self):
        if self.var_dep.get()=="" or self.var_email.get()=="":
            messagebox.showerror('Error','All Fields are required')
        else:
            try:
                update=messagebox.askyesno('update','Are you sure update this employee data')
                if update>0:
                  conn=mysql.connector.connect(host='localhost',username='root',password='AMIYA#84#gudu',database='first_proj')
                  my_cursor=conn.cursor()
                  my_cursor.execute('update employee1 set Department=%s,Name=%s,Designition=%s,Email=%s,Address=%s,Marraid_status=%s,DOB=%s,DOJ=%s, id_proof_type=%s,Gender=%s,Phone=%s,Country=%s, Salary=%s where id_proof=%s',(
                      
                                                                                                                                                                                                                                self.var_dep.get(),
                                                                                                                                                                                                                                self.var_name.get(),
                                                                                                                                                                                                                                self.var_designition.get(),
                                                                                                                                                                                                                                self.var_email.get(),
                                                                                                                                                                                                                                self.var_address.get(),
                                                                                                                                                                                                                                self.var_married.get(),
                                                                                                                                                                                                                                self.var_dob.get(),
                                                                                                                                                                                                                                self.var_doj.get(),
                                                                                                                                                                                                                                self.var_idproofcomb.get(),                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     self.var_idproof.get(),
                                                                                                                                                                                                                                self.var_gender.get(),
                                                                                                                                                                                                                                self.var_phone.get(),
                                                                                                                                                                                                                                self.var_salary.get(),
                                                                                                                                                                                                                                self.var_country.get(),
                                                                                                                                                                                                                                self.var_idproof.get()

                                                                                                                                                                                                                            ))
                else:
                    if not update:
                        return
                conn.commit()
                self.fetch_data()
                conn.close()
                messagebox.showinfo('success','Employee Successfully updated',parent=self.root)
            except Exception as es:
                messagebox.showerror('Error',f'Due To:{str(es)})',parent=self.root)

    # Delete
    def delete_data(self):
        if self.var_idproof.get()=="":
            messagebox.showerror('Error',"All fields are required")
        else:
            try:
                Delete=messagebox.askyesno('Delete','Are you sure to delete this employee',parent=self.root)
                if Delete>0:
                  conn=mysql.connector.connect(host='localhost',username='root',password='AMIYA#84#gudu',database='first_proj')
                  my_cursor=conn.cursor()
                  sql='delete from employee1 where idproof=%s'
                  value = (self.var_idproof.get(),)
                  my_cursor.execute(sql,value)
                else:
                    if not Delete:
                        return
                    conn.commit()
                    self.fetch_data()
                    conn.close()
                    messagebox.showinfo('Delete','Employee Successfully Deleted',parent=self.root)
            except Exception as es:
                messagebox.showerror('Error',f'Due To:{str(es)})',parent=self.root)



if __name__== "__main__": 
    root=Tk()
    obj=Employee(root)
    root.mainloop()
        
