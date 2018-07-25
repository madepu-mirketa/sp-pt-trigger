node {
	println ""

	def state=env.state
	def everything=env.everything

	println "everthing:"+everything
	println "state:"+state
	if(state.equals("finished")){
		stage('CI build'){
			build 'sp-ci'
		}
	}
	if(state.equals("accepted")){
		stage('Release build'){
			build 'sp-release'
		}
	}
}