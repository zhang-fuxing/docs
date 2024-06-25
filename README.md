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
