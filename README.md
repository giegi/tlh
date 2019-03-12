<h2>TLH</h2><br />
<p><b>tlh</b> stands for Traffic Light Handler. <br />
You might never need this tool in your whole programmer life. Most of the web developers won't have the need to use a library download manager to handle which library to load first, and which libraries need to be waited before downloading another one. Many developers won't need to wait data from three, four, five other javascript sources.<br />
But if you might need to do this, tlh is right for you.<br />
TLH is a js/css library download handler for complex javascript ecosystems. </p>
<p>Let's draw a scenario.<br />
An analytics system, in order to work properly, needs to have available a serie of objects and informations in page. These objects have different sources. A javascript library, the result of an asynchronous ajax call, the acceptance of the Gdpr Infoprivacy, the analytics sdk, its initialization.<br />
Putting in order the script tags in the head tag is not enough to be sure that everything will work in the correct sequence.
TLH does this for you. <br />
Let's see a pratical example.</p>

<code>
  // Let's setup the sources of data and our main object<br />
kw_tlh_configs.webtrekk_premium_manager = tlhControlObject(objectCallback, "https://www.urltoload.com/jstoload.js", onloadSuccessCallback, onloadErrorCallback, asyncLoad); // this will be an ajax call <br /> 
kw_tlh_configs.webtrekk_mapping = tlhControlObject(objectCallback, "https://www.urltoload.com/jstoload.js", onloadSuccessCallback, onloadErrorCallback, asyncLoad); // This is the mapping json info<br />
kw_tlh_configs.webtrekk = tlhControlObject(objectCallback, "https://www.urltoload.com/jstoload.js", onloadSuccessCallback, onloadErrorCallback, asyncLoad); // This is the main object<br />
  
  // Let's assume we already have setup an object called adsetup before in the page<br />
  
  // Let's create the premium info source (the result of an ajax call in the end) and its dependency from adsetup object<br />
  window.kw_tlh.webtrekk_premium_manager = new tlhl("webtrekk_premium_manager", kw_tlh_configs.webtrekk_premium_manager);<br />
  window.kw_tlh.webtrekk_premium_manager.addLibRedLight("adsetup", window.kw_tlh.adsetup);        <br />
	window.kw_tlh.webtrekk_premium_manager.addRedLight("premium_data_formatted");       <br /> 
  
  // Let's create the mapping entity and its dependency from adsetup object<br />
  window.kw_tlh.webtrekk_mapping = new tlhl("webtrekk_mapping", kw_tlh_configs.webtrekk_mapping);<br />
  window.kw_tlh.webtrekk_mapping.addLibRedLight("adsetup", window.kw_tlh.adsetup);<br />
  
  // Let's complete the main object defining its dependencies <br />
  window.kw_tlh.webtrekk = new tlhl("webtrekk", kw_tlh_configs.webtrekk);		<br />
  window.kw_tlh.webtrekk.addLibRedLight("webtrekk_premium_manager", window.kw_tlh.webtrekk_premium_manager);	<br />
  window.kw_tlh.webtrekk.addLibRedLight("webtrekk_mapping", window.kw_tlh.webtrekk_mapping);<br />
  window.kw_tlh.webtrekk.addLibRedLight("adsetup", window.kw_tlh.adsetup);    <br />
  window.kw_tlh.webtrekk.addRedLight("wt_init");<br />
  window.kw_tlh.webtrekk.addRedLight("wt_send");<br />
  
  </code>
