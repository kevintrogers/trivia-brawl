<template name='luchadorCreateForm'>
    <div>
    <div class='luchador-create col-12 '>
        <form id='luchador-create-form'>
            <div class='form-group col-xs-10 col-xs-offset-1'>
                <label for='luchador-name'>Name of Fighter</label>
                <input type='text' class='form-control' id='luchadorName'>
            </div>
            <div class='row'>
                <div class='form-group col-xs-4 col-xs-offset-1 '>
                    <label for='luchador-height'>Height (In Inches)</label>
                    <input class='' type='number' value='68' min='40' max='120' class='form-control' id='luchadorHeight'>
                </div>
                
                <div class='form-group col-xs-4 col-xs-offset-1'>
                    <label for='luchador-weight'>Weight (In Pounds)</label>
                    <input type='number' value='200' min='75' max='999' class='form-control' id='luchadorWeight'>
                </div>
            </div>
            <div class='row'>
                <div class='form-group col-xs-4 col-xs-offset-1'>
                    <label for='luchador-mask-color'>Mask Color</label><br>
                    <select class="custom-select" id='mainColor' v-model='maskColor'>
                      <option selected>Choose Mask Color</option>
                      <option v-for='color in colors' :style='{color:color}'>{{color}}</option>
                    </select>
                    
                </div>
                <div class='form-group col-xs-4 col-xs-offset-1'>
                    <label for='luchador-trim-color'>Trim Color</label><br>
                    <select class="custom-select" id='trimColor' v-model='trimColor'>
                      <option selected>Choose Trim Color</option>
                      <option v-for='color in colors' :style='{color:color}'>{{color}}</option>
                    </select>
                  
                </div>
            </div> 
            <div class='row'>
            <div class='form-group col-xs-4 col-xs-offset-1'>
                <label for='luchador-eye-color'>Eye Color</label><br>
                <select class="custom-select" id='eyeColor' v-model='eyeColor'>
                  <option selected>Choose Eye Color</option>
                  <option v-for='eye in eyes' :style='{color:eye}'>{{eye}}</option>
                </select>
              
              </div>
                    <div class='form-group col-xs-4 col-xs-offset-1'>
                <label for='luchador-mask-style'>Mask Style</label><br> 
                <select class="custom-select" id='maskStyle' v-model='maskStyle'>
                  <option selected>Choose Mask Style</option>
                  <option v-for='style in styles'>{{style}}</option>
                 </select>
              
              </div>

              </div>
              <div class='row btn-row'>
                  <button class='btn btn-primary'type='button' @click='setLuchador'>Create</button>
              </div>
             </form> 
             
            
            </div>
               <div class='box'>
    	<div class='head' :style="{background:maskColor}">
			<div class='mask'>
				<div class='mask mask-left' :style="{background:trimColor}"></div>
				<div class='mask mask-top'></div>
				<div class='mask mask-right' :style="{background:trimColor}"></div>
				<div class='ear-left'></div>
				<div class='ear-right'></div>
		<div class='lens-left-border'>
				<div class='mask lens-left' :style="{background:trimColor}"></div>
				</div>
					<div class='eye eye-left'><div class='brow'></div><div class='iris' :style="{background:eyeColor}"><div class='pupil'></div></div></div>
			
				
				<div class='lens-right-border'> 
					<div class='mask lens-right' :style="{background:trimColor}"></div>	
					</div>
					<div class='eye eye-right'><div class='brow'></div><div class='iris' :style="{background:eyeColor}"><div class='pupil'></div></div></div>
		
				<div class='glasses frame-right'></div>
				<div class='nose'></div>
				<div class='upper-lip'></div>
				<div class='teeth'></div>
				<div class='lower-lip'>
					
			</div>

			<div class='singlet' :style="{background:maskColor}"></div>
			<div class='neck'></div>
			
				
				<div class='shoulder-left'></div>
				<div class='upper-arm-left'></div>
				<div class='fore-arm-left'></div>
				<div class='hand-left'></div>
				
				<div class='shoulder-right'></div>
					<div class='upper-arm-right'></div>
					<div class='fore-arm-right'></div>
					<div class='hand-right'></div>
					<div class='top-pack-left'></div><div class='top-pack-right'></div>
					<div class='middle-pack-left'></div><div class='middle-pack-right'></div>
					<div class='bottom-pack-left'></div><div class='bottom-pack-right'></div>
					<div class='row belt'>
					<div class='medallion valign-wrapper '><span class='center valign'>CHAMPION</span></div>
					</div>
					</div>			
	    </div>
	</div>
	</div>
        
    
</template>
<script>


export default {
    data() {
        return {
            maskColor: '',
            trimColor: '',
            eyeColor: '',
            maskStyle: '',
            colors: ['orange','yellow','red','green','purple','blue','black','white'],
            eyes: ['lightblue', 'lightgreen', 'blue', 'lightgrey', 'green', 'brown', 'black', 'red'],
            styles: ['Classic', 'Beast', 'Chupacabra', 'Pretty Boy', 'Royal', 'Razzle Dazzle', 'Fabulous', 'Demon']
        };
    },
    
        methods: {
            setLuchador: function () {
                var name = document.getElementById('luchadorName').text.value, 
                height = document.getElementById('luchadorHeight').value, 
                weight = document.getElementById('luchadorWeight').value, 
                mainColor = document.getElementById('mainColor').value, 
                trimColor = document.getElementById('trimColor').value,
                eyeColor = document.getElementById('eyeColor').value,
                maskStyle = document.getElementById('maskStyle').value,
                luchador = { 'name': name, 
                            'height': height, 
                            'weight': weight, 
                            'mainColor': mainColor, 
                            'trimColor': trimColor, 
                            'eyeColor': eyeColor, 
                            'maskStyle': maskStyle };
                
                
                Meteor.call('addLuchador', luchador);
            
            }
        }
    };



    
</script>
