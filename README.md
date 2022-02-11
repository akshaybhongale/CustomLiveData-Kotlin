# CustomLiveData-Kotlin with ConnectivityManager

Required permissions :
--
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.CHANGE_NETWORK_STATE" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
    
Usage :
--
    /**
     * Network request
     */
    private val mNetworkRequest = NetworkRequest.Builder()
        .addCapability(NetworkCapabilities.NET_CAPABILITY_INTERNET)
        .addTransportType(NetworkCapabilities.TRANSPORT_WIFI)
        .addTransportType(NetworkCapabilities.TRANSPORT_CELLULAR)
        .build()
    
    /**
     * live data instance
     */
    private val mNetworkState: NetworkLiveData = NetworkLiveData(applicationContext,mNetworkRequest)

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
       
       mNetworkState.observe(this, {
            if(!it){
                Toast.makeText(this,"Please check internet connection",Toast.LENGTH_SHORT).show()
            }else{
                // make server call
            }  
        })
    }
