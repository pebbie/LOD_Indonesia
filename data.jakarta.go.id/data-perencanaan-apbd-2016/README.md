# Data Perencanaan APBD 2016 dalam RDF

```
12/01/2015  02:25 PM         1,582,585 KUA-PPAS-2016-csv.openrefine.tar.gz

12/01/2015  01:58 PM        16,914,691 KUA-PPAS-2016-csv.ttl

12/01/2015  02:25 PM         3,102,994 KUA-PPAS-2016-history-csv.openrefine.tar.gz

12/01/2015  02:23 PM        17,344,234 KUA-PPAS-2016-history-csv.ttl

12/01/2015  02:24 PM         1,968,942 RKPD-2016-csv.openrefine.tar.gz

12/01/2015  01:44 PM        13,406,277 RKPD-2016-csv.ttl

               7 File(s)     54,319,723 bytes
```

## Panduan Unggah di Virtuoso
* unggah masing-masing file .ttl ke graf yang berbeda (misal Graph URI : `http://data.jakarta.go.id/rkpd/2016/` untuk file `RKPD-2016-csv.ttl`)

## Kueri-kueri

```
PREFIX jkt: <http://data.jakarta.go.id/ontology/>

SELECT ?g ?skpd SUM(?amt) as ?anggaran 
WHERE { 

GRAPH ?g { 
?skpd a jkt:SKPD .
?keg jkt:unitPengaju ?skpd .
?keg jkt:anggaran ?amt
} 

} 
GROUP BY ?g ?skpd
ORDER BY ASC(?skpd) DESC(?g)
LIMIT 500
```

```
PREFIX jkt: <http://data.jakarta.go.id/ontology/>

SELECT (?skpd1 as ?skpd) ?namaskpd (SUM(?amt1) as ?anggaran) (SUM(?amt2) as ?plafon) (?plafon-?anggaran as ?delta) 
WHERE { 

GRAPH <http://data.jakarta.go.id/rkpd/2016/> { 
?keg1 jkt:unitPengaju ?skpd1 .
?skpd1 rdfs:label ?namaskpd .
?keg1 jkt:anggaran ?amt1
} 

GRAPH <http://data.jakarta.go.id/kua-ppas/2016/> { 
?keg2 jkt:unitPengaju ?skpd2 .
?keg2 jkt:anggaran ?amt2
} 

FILTER(?skpd1=?skpd2)
}
ORDER BY DESC(?anggaran) ASC(?skpd1)
LIMIT 100
```