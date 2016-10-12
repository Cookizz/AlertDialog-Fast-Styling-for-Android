# AlertDialog-Fast-Styling
Some visual parts of `android.support.v7.AlertDialog` can be fastly styled by inheriting its base theme instead of customizing new layouts, which is considered clumsy. Modifying these visual parts still agrees with Material Design.

## Requirement

      dependencies {
          compile 'com.android.support:appcompat-v7:22.2.0'
      }

## Approach

  1. Fork the following style xml code into your `styles.xml` and modify their value as you want.

        <style name="AlertDialogFastStyling" parent="Theme.AppCompat.Light.Dialog.Alert">
              <item name="android:textColorPrimary">@color/abc_primary_text_material_light</item>
              <item name="android:windowTitleStyle">@style/AlertDialogFastStyling.Title</item>
              <item name="android:windowBackground">@drawable/abc_dialog_material_background_light</item>
      
              <item name="listPreferredItemPaddingLeft">24dp</item>
              <item name="listPreferredItemPaddingRight">24dp</item>
      
              <item name="buttonBarButtonStyle">@style/AlertDialogFastStyling.Button</item>
      
              <item name="android:listChoiceIndicatorSingle">@drawable/abc_btn_radio_material</item>
              <item name="android:listChoiceIndicatorMultiple">@drawable/abc_btn_check_material</item>
          </style>
      
          <style name="AlertDialogFastStyling.Title" parent="RtlOverlay.DialogWindowTitle.AppCompat">
              <item name="android:textAppearance">@style/AlertDialogFastStyling.Title.TextAppearance</item>
          </style>
          <style name="AlertDialogFastStyling.Title.TextAppearance">
              <item name="android:textSize">@dimen/abc_text_size_title_material</item>
              <item name="android:textColor">@color/abc_primary_text_material_light</item>
          </style>
          <style name="AlertDialogFastStyling.Button" parent="Widget.AppCompat.Button.ButtonBar.AlertDialog">
              <item name="android:textColor">#009688</item>
              <item name="android:textSize">14sp</item>
          </style>

  2. Use `AlertDialogFastStyling` while building `AlertDialog` component. The following samples are available for testing and their insets show the visual mappings to style items in `AlertDialogFastStyling`.

  ##### Confirm Dialog
  
        AlertDialog dialog = new AlertDialog.Builder(context, R.style.AlertDialogFastStyling)
                .setTitle("提醒")
                .setPositiveButton("是", null)
                .setNegativeButton("否", null)
                .setMessage("检测到距离您上次清理已超过30天，是否立即清理？")
                .show();
  
  ![confirm dialog](https://github.com/Cookizz/AlertDialog-Fast-Styling/blob/master/art/confirmdialog.png)
  
  ===
  ##### Choice Dialog
  
        AlertDialog dialog = new AlertDialog.Builder(context, R.style.AlertDialogFastStyling)
                .setItems(new String[] {"布丁味的老人茶", "奶昔", "巴拿拿牌烤香蕉"},
                        new DialogInterface.OnClickListener() {
                            @Override
                            public void onClick(DialogInterface dialog, int which) {
                                dialog.cancel();
                            }
                })
                .show();
                        
  ![confirm dialog](https://github.com/Cookizz/AlertDialog-Fast-Styling/blob/master/art/choicedialog.png)
  
  ===
  ##### Radio Dialog
  
        AlertDialog dialog = new AlertDialog.Builder(context, R.style.AlertDialogFastStyling)
                .setSingleChoiceItems(new String[] {"布丁味的老人茶", "奶昔", "巴拿拿牌烤香蕉"}, 0, null)
                .setPositiveButton("确定", null)
                .setNegativeButton("取消", null)
                .show();
                        
  ![confirm dialog](https://github.com/Cookizz/AlertDialog-Fast-Styling/blob/master/art/radiodialog.png)
  
  ===
  ##### Check Dialog
  
        AlertDialog dialog = new AlertDialog.Builder(context, R.style.AlertDialogFastStyling)
                .setMultiChoiceItems(new String[] {"布丁味的老人茶", "奶昔", "巴拿拿牌烤香蕉"},
                        new boolean[] {false, true, true},
                        null)
                .setPositiveButton("确定", null)
                .setNegativeButton("取消", null)
                .show();
                        
  ![confirm dialog](https://github.com/Cookizz/AlertDialog-Fast-Styling/blob/master/art/checkdialog.png)
  
