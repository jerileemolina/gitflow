pipeline {
    agent any
    stages {
        stage("release groovy") {
            steps{
                echo ""
                script {
                    //sacar contenido del release.yml en una variable release
                    def release = readYaml (file: 'release.yml')
                    //para saber que tipo de variable es (la variable es tipo de HashMap)
                    println release.getClass().getName()
                    
                    def nombre = "APP_JAVA_AUX"
                    def version = "1.0.5"
                    //Mostrar que ha hecho el cambio en la variable
                    def añadir = 1
                    release.each{k,v->
                        if (nombre == k){
                            println "La versión de " + k + " era " + v "y ahora es " + version
                            añadir = 0
                        } else {
                            println "La versión de " + k + " es " + v
                        }
                    }

                    if (añadir == 1 ) {
                        println "La versión de " + nombre + " es " + version
                    }
                        

                    // Cambio valores de la variable release (tipo HashMap)
                    release.put(nombre, version)

                    // Meter los datos de la variable en un archivo nuevo llamado igual, y lo sobreescribe
                    //WriteYaml Overwrite)
                    writeYaml file: "release.yml", data: release, overwrite: true
                    

                }
            }
        }
    }
}

