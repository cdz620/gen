
## Important

This project was forked from smallnest/gen. Removes table name and struct singular. The origin project is [db2struct](https://github.com/Shelnutt2/db2struct)
git diff: 
```
--- a/main.go
+++ b/main.go
@@ -110,7 +110,6 @@ func main() {
        // generate go files for each table
        for _, tableName := range tables {
                structName := dbmeta.FmtFieldName(tableName)
-               structName = inflection.Singular(structName)
                structNames = append(structNames, structName)

                modelInfo := dbmeta.GenerateStruct(db, tableName, structName, "model", *jsonAnnotation, *gormAnnotation, *gureguTypes)
@@ -126,7 +125,7 @@ func main() {
                        fmt.Println("Error in formating source: " + err.Error())
                        return
                }
-               ioutil.WriteFile(filepath.Join("model", inflection.Singular(tableName)+".go"), data, 0777)
+               ioutil.WriteFile(filepath.Join("model", tableName+".go"), data, 0777)

                if *rest {
                        //write api
```
