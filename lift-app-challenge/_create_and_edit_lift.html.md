## Creating and editing a lift
Now that we have designed the basic layout for MainActivity we will proceed to design an UI for creating and editing a lift in **CreateLiftActivity**.
A lift entity consists of four attributes:
* Phone number: The phone number of the car owner.
* Location: The initial location of the lift.
* Start time from home : The departure time from the location.
* Start time from office : The departure time from the office.

For the UI of **CreateLiftActivity**, create a new xml file called **activity_create_lift.xml** and paste the code into the file shown below.

    <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin" >

    <ScrollView
        android:id="@+id/Scrollview"
        android:layout_width="fill_parent"
        android:layout_height="fill_parent" >

        <LinearLayout
            android:id="@+id/LLayout02"
            android:layout_width="fill_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical" >

            <LinearLayout
                android:id="@+id/phn_block"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_marginTop="30dp"
                android:orientation="horizontal" >

                <TextView
                    android:id="@+id/phn"
                    android:layout_width="0dp"
                    android:layout_height="wrap_content"
                    android:layout_weight="35"
                    android:text="@string/lbl_phn" />

                <EditText
                    android:id="@+id/fld_phn"
                    android:layout_width="0dp"
                    android:layout_height="wrap_content"
                    android:layout_weight="65"
                    android:hint="@string/lbl_enter_phn"
                    android:inputType="textPhonetic" />
            </LinearLayout>

            <LinearLayout
                android:id="@+id/location_block"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:orientation="horizontal" >

                <TextView
                    android:id="@+id/location"
                    android:layout_width="0dp"
                    android:layout_height="wrap_content"
                    android:layout_weight="35"
                    android:text="@string/lbl_location" />

                <EditText
                    android:id="@+id/fld_location"
                    android:layout_width="0dp"
                    android:layout_height="wrap_content"
                    android:layout_weight="65"
                    android:hint="@string/lbl_enter_location"
                    android:inputType="textPhonetic" />
            </LinearLayout>

            <View
                android:layout_width="match_parent"
                android:layout_height="1dp"
                android:background="#666666" />

            <LinearLayout
                android:id="@+id/stime_block"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:orientation="horizontal" >

                <TextView
                    android:id="@+id/stime"
                    android:layout_width="0dp"
                    android:layout_height="wrap_content"
                    android:layout_gravity="center_vertical"
                    android:layout_weight="20"
                    android:text="@string/lbl_stime" />

                <TimePicker
                    android:id="@+id/fld_stime"
                    android:layout_width="0dp"
                    android:layout_height="wrap_content"
                    android:layout_weight="80" />
            </LinearLayout>

            <View
                android:layout_width="match_parent"
                android:layout_height="1dp"
                android:background="#666666" />

            <LinearLayout
                android:id="@+id/etime_block"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:orientation="horizontal" >

                <TextView
                    android:id="@+id/etime"
                    android:layout_width="0dp"
                    android:layout_height="wrap_content"
                    android:layout_gravity="center_vertical"
                    android:layout_weight="20"
                    android:text="@string/lbl_etime" />

                <TimePicker
                    android:id="@+id/fld_etime"
                    android:layout_width="0dp"
                    android:layout_height="wrap_content"
                    android:layout_weight="80" />
            </LinearLayout>

            <View
                android:layout_width="match_parent"
                android:layout_height="1dp"
                android:background="#666666" />

            <Button
                android:id="@+id/lift_submit"
                android:layout_width="200dp"
                android:layout_height="wrap_content"
                android:layout_gravity="center"
                android:text="@string/lbl_create" />
        </LinearLayout>
    </ScrollView>
    </RelativeLayout>

You should now have a layout looking like this:


##Tasks

1. Make MainActivity a one time post-install activty. When the user opens the app for the second time the MainActivity should be skipped to the LiftListActivity.
2. In CreateLiftActivity, store the lift details entered by the user in SharedPreference. We need to mandate that you store the token details in your app in **codelearn_liftapp** SharedPreference with keys **key_pref_phone** for the phone number, **key_pref_location** for the location, **key_pref_stime** for the start time from home & **key_pref_etime** for the start time from office.
3. Add a menu item to LiftListActivity which allows the user to edit/create the lift details. The user should be presented with the create lift screen with the fields populated with the lift details if a lift has already been created or left empty if not. The user should then be able to edit the lift details or create a new one.

##Restrictions
1. The lift data must be stored in a SharedPreference file named "codelearn_liftapp".
2. The start from home and start from office values retrieved from the TimePicker views must be stored in the format: **"HH:mm"**.
3. The resource file for populating the menu in LiftListActivity should be named **lift_list.xml**.
