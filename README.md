
age_label.grid(row=2,column=0)
address_label=Label(root=3,column=0)
address_label.grid(row=3,column=0)
email_label=Label(root,text="pumarinjade@gmail.com")
email_label.grid(row=4,column=0)

submit_btn=Button(root,text="Add Record to Database",command=submit)
submit_btn.grid(row=6,column=0,columnspan=2,pady=10,padx=10,ipadx=100)

query_btn=Button(root,text="Show records",command=query)
query_btn.grid(row=7,column=0,columnspan=2,pady=10,padx=10,ipadx=137)

conn=sqlite3.connect('C:/Users/STUDENT2')
c=conn.cursor()
c.execute("""CREATE TABLE "myinfo"
	("f name"   TEXT,
	"l name"    TEXT,
	"age"	INTEGER,
	"address"   TEXT,
	"email"	TEXT
         )"""
)
def submit():
    conn=sqlite3.connect('C:/Users/CICT/data.db')
    c=conn.cursor()
    c.execute("INSERT INTO studentinfo VALUES(:f_name,:age,:address,:email)",
              {
                  'f_name':f_name.get(),
                  '_name':_name.get(),
                  'age':age.get(),
                  'address':address.get(),
                  'email':email.get(),
                  })
    conn.commit
    conn.close
    f_name.delete(0,END)
    l_name.delete(,END)
    age.delete(0,END)
    address.delete(0,END)
    email.delete(0,END)
    

