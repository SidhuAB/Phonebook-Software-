# Phonebook-Software-
Implementation of Phonebook using Hash Maps with insert, delete, update, search through keyword  other features.
#include<unordered_map>
#include<iostream>
using namespace std;
  	unordered_map<string,string> map;
  	unordered_map<string,string>::iterator it;
  
    
    void cool_search(string name,int len){
    
    	it=map.begin();
    	int i;
    	while(it!=map.end()){
    		for(i=0;i<len;i++){
    			if(name[i]==it->first[i]){
    				continue;
				}
				else{
					break;
				}
			}
			if(i==len){
			  cout<<it->first<<" "<<it->second<<endl;	
			}
			it++;
		}
		cout<<endl;
    	return ;
	}
    
  void update(string name){
  	if(map.count(name)>0){
  		string new_name;
  		string new_con;
  		cout<<"Press 1 to update name:"<<endl;
  		cout<<"Press 2 to update number:"<<endl;
  		int choice;
  		cin>>choice;
  		if(choice==1){
  				cout<<"Enter new name: ";
  				cin>>new_name;
  				 it=map.begin();
    			while(it!=map.end()){
    				if(it->first==name){
    				  new_con=it->second;
					}
    			 it++;
  				}
  			  map.erase(name);
				map[new_name]=new_con;  
				cout<<endl<<"Updated Successfully"<<endl<<endl;
  			    return ;
  			}
  		else if(choice==2){
  			cout<<"Enter new no: ";
  			cin>>new_con;
  			 while(new_con.size()!=10){
	     		    	cout<<"Please enter 10 digit no: ";
	     		    	cin>>new_con;
					 }
  			map[name]=new_con;
  			cout<<endl<<"Updated Successfully"<<endl<<endl;
  			return ;
		  }	
	
	  }
	else{
	 	cout<<endl<<endl<<"Contact not found!"<<endl<<endl;
		return ;	
	}  
  }
  
  void delete_cont(string name){
  	
  	if(map.count(name)>0){
  		map.erase(name);
  		cout<<endl<<endl<<"Deleted Successfully!"<<endl<<endl;
  		return ;
	  }
	else{
		cout<<endl<<endl<<"Contact not found!"<<endl<<endl;
		return ;
	}
  	
  }
  
  bool search(string name){
    it=map.begin();
    while(it!=map.end()){
    if(it->first==name){
    	cout<<endl<<"Name:"<<it->first<<endl<<"Phone no:"<<it->second<<endl<<endl;
    	return true;
	}
     it++;
  }
  return false;
  }
  
  
  void insert(string name,string number){
  	
  	if(map.count(name)>0){
  		char ch;
  		cout<<"Name already exist"<<endl;
  		cout<<"Do you want to update:(Y/N): ";
  		cin>>ch;
  		if(ch=='Y'){
  		    cout<<"Enter no.: ";
	     		    cin>>number;
	     		    while(number.size()!=10){
	     		    	cout<<"Please enter 10 digit no: ";
	     		    	cin>>number;
					 }
			map[name]=number;
			cout<<endl<<"Updated Successfully"<<endl<<endl;
			return ;		 
		  }
		  else{
		  	return ;
		  }
    }
	  else{
  	map[name]=number;
  	return ;
         }
  }

int main(){
	cout<<":Welcome To PhoneBook:"<<endl<<endl;
	while(1){
		int choice;
		int len;
		 cout<<"Press 1 to insert: "<<endl;
        cout<<"Press 2 to search: "<<endl;
         cout<<"Press 3 to delete: "<<endl;
           cout<<"Press 4 to update: "<<endl;
           cout<<"Press 5 to cool search: "<<endl;
            cout<<"Press 6 to exit: "<<endl;
		string name;
		int ans;
		string number;
		cin>>choice;
	     switch(choice){
	     	
	     	case 1: 
	     		    cout<<"Enter name: ";
	     		    cin>>name;
	     		    cout<<"Enter no: ";
	     		    cin>>number;
	     		    while(number.size()!=10){
	     		    	cout<<"Please enter 10 digit no: ";
	     		    	cin>>number;
					 }
	  				insert(name,number);
	  				break;
	  		case 2:
	  			    cout<<"Enter name to search: ";
	  			    cin>>name;
			   		 ans=search(name);
			   		if(!ans)
			   			cout<<endl<<"Result Not Found"<<endl<<endl;
			   			else
			   			continue;
			   		break;
			case 3:
                   cout<<"Enter the contact name you want to delete: ";
				   cin>>name;
				   delete_cont(name);	
				   break;		         		
			case 4:
			       cout<<"Enter contact you want to update: ";
				   cin>>name;
				   update(name);
				   break;       
		    case 5:
		    	 cout<<"Enter keyword to search: ";
		    	 cin>>name;
		    	 len=name.size();
		    	 cool_search(name,len);
		    	 break;
		    	 
		    case 6:
			    return 0;	
		 }
	}
}
