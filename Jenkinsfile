node {
	println ""

	def pt_current_state=env.pt_current_state
	def pt_everything=env.pt_everything

	println "everthing:"+pt_everything
	println "state:"+pt_current_state
	def pt_story_id=0
	if(pt_kind.equals("story")){
		pt_story_id=env.pt_id
	}	
	if(pt_current_state.equals("finished")){
		stage('CI build'){
			if(pt_story_id!=0) {
				build job: 'sp-ci', parameters: [string(name: 'story_id', value: pt_story_id)]
			}
		}
	}
	if(pt_current_state.equals("delivered")){
		stage('Release QA build'){
			if(pt_story_id!=0) {
				build 'sp-release'
			}		
		}
	}	
	if(pt_current_state.equals("accepted")){
		stage('Release UAT build'){
			if(pt_story_id!=0) {
				build 'sp-release'
			}	
		}
	}
}