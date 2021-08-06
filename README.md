# announecent-banner
//Notification banner display per session (cookie)  
  
//select your banner element 
const banner = document.querySelector('.bar-wrapper');

//select your x closed buttin element
const closeLink = document.querySelector('.announcement-bar')

function closeBanner() {
	sessionStorage.setItem('bannerClosed', 'true');
    $(banner).hide();
}

if (sessionStorage.getItem('bannerClosed') != 'true') {
	$(banner).css('display','flex')
	$(closeLink).click(function(){
	closeBanner();
	})
}
  
window.onbeforeunload = function(){
    sessionStorage.setItem("origin", window.location.href);
}
window.onload = function(){
    if(window.location.href == sessionStorage.getItem("origin")){
        sessionStorage.clear();
    }
}

