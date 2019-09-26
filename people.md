# Creacion base de datos gzip

(dentro carpeta bin) mongorestore --gzip --db personas dump/people.bson.gz

# MAP

 let map = function(){
     emit(this.name,this.points)
        };

 # REDUCE

  let reduce = function(name,points){
      return Array.sum(points);
        };

  # mapReduce

  db.people.mapReduce(map,
                      reduce, 
                      {out: "totales"});

# resultado

{
        "result" : "totales",
        "timeMillis" : 7791,
        "counts" : {
                "input" : 1000000,
                "emit" : 1000000,
                "reduce" : 86684,
                "output" : 26
        },
        "ok" : 1
}