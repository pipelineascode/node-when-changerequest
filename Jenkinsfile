node{

stage('Build'){

checkout([$class: 'GitSCM', 				
					branches: [[name: "origin/master"]], 
					userRemoteConfigs: [[
					url: 'https://github.com/pipelineascode/node-when-changeset.git']]
					])


def changesetFound = false					
def changeLogSets = currentBuild.changeSets
println  "changeLogSets.size(): ${changeLogSets.size()}"
for (int i = 0; i < changeLogSets.size(); i++) {
    def entries = changeLogSets[i].items
    for (int j = 0; j < entries.length; j++) {
        def entry = entries[j]
        def files = new ArrayList(entry.affectedFiles)
        for (int k = 0; k < files.size(); k++) {
            def file = files[k]
			if (file.path.endsWith(".js")){
				changesetFound = true;
				break;
			}
            echo "${file.path}"
        }
		
		if(changesetFound)
			break;
    }
}

echo "changesetFound:${changesetFound}"
}
}



