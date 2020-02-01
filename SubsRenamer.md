'''
@author: Misho
'''


import os, time


class Test():
    
    root_path = "M:"
    #root_path = "D:/test"
    counter = 0
    
    def main(self):
        
        folderlist = os.listdir(self.root_path)
        t1 = time.time() 
        
        for el in folderlist:
        
            path_folder = "%s/%s"%(self.root_path, el)
            print (path_folder)
            
            if os.path.isdir(path_folder):
                #print ("Yes")
                self.Folder_work(path_folder)
            else:
                #print ("No")
                self.File_work(path_folder)
            #print (20*"=")
        print (20*"=")
        print ("time:", time.time()-t1)
        print ("counter:", self.counter)   
            
            
    def Folder_work(self, folder):
        
        #print ("working with ...", folder)
        
        folderlist = os.listdir(folder)
        
        for el in folderlist:
            #print (folders)
            path_folder = "%s/%s"%(folder, el)
            #print (path_folder)
            
            if os.path.isdir(path_folder):
                #print ("Yes")
                self.Folder_work(path_folder)
            else:
                #print ("No")
                self.File_work(path_folder)
            #print (20*"-")
        
        
    def File_work(self, file_path):
        
        if str(file_path).endswith(".srt") and not str(file_path).endswith(".bg.srt") and not str(file_path).endswith(".en.srt"):
            print ("Found:", file_path)
            self.counter+=1
            
            new_path = "%s.bg.srt"%str(file_path)[:-4]
            print ("Renamed:", new_path)
            self.Rename_file(file_path, new_path)
                
        
        elif str(file_path).endswith(".sub") and not str(file_path).endswith(".bg.sub") and not str(file_path).endswith(".en.sub"):
            print ("Found:", file_path)
            self.counter+=1
            
            new_path = "%s.bg.sub"%str(file_path)[:-4]
            print ("Renamed:", new_path)   
            self.Rename_file(file_path, new_path)
    
    
    def Rename_file(self, file_path, new_path):
        
        try:
            os.rename(file_path, new_path)
        except:
            print ("problem")    
    
    
t = Test()
t.main()
