```
select '/'
           ||
       p."Project_Name_En"
           ||
       '/'
           ||
       case
           when t."DocTypeMark" = 72 then '导航资料'
           else '仪器资料'
           end
           ||
       '/'
           ||
       t."TypeName"     dest,
       v."FileNamePath" source
from "VGeoData" v
         inner join "Project" p on v."Projectid" = p."ProjectID"
         inner join "VPicsType" t on v."PicsTypeID" = t."PicsTypeID"
where t."DocTypeMark" in (72, 73)
  and "ExplainProcessSign" = 3
order by v."Projectid";
```
```java
    static void bakFile(String bakPath, String inputFilePath) throws IOException {
        String line;
        try (BufferedReader br = Files.newBufferedReader(Path.of(inputFilePath))) {
            while ((line = br.readLine()) != null) {
                String relPath = line.substring(0, line.indexOf(","));
                String absPath = line.substring(line.indexOf(",") + 1);
                absPath = absPath.replace("\"", "");
                if (!absPath.startsWith("/")) {
                    absPath = "/hwdata/FileShare/" + absPath;
                }
                try {
                    Path path = Path.of(absPath);
                    String target = bakPath + relPath;
                    if (!Files.exists(Path.of(target))) {
                        Files.createDirectories(Path.of(target));
                    }
                    Files.copy(path, Path.of(target + "/" + path.getFileName()));
                } catch (IOException e) {
                    System.out.println(e.getMessage());
                }

            }

        }
    }
```

