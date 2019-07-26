To get the current phone number already connected to the call you need to use [Call.Details#getHandle()][1].

So inside your `onScreenCall` :

    @Override
    public void onScreenCall(Call.Details callDetails) {
       Log.i("Phone number", callDetails.getHandle().toString());
    }
    
    
See Full Answer [here][2]

  [1]: https://android.googlesource.com/platform/frameworks/base/+/refs/heads/master/telecomm/java/android/telecom/Call.java#724
  [2]: https://stackoverflow.com/questions/56813810/how-to-extract-phone-number-from-call-details-in-callscreeningservice/57139101#57139101
  
