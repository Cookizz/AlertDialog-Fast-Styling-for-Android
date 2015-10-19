# AlertDialog-Fast-Styling
Some parts of android.support.v7.AlertDialog can be styled very easily. It is stupid to recreate a custom layout.

## Approach

  1. Fork styles of `style.xml` into your project and redefine their value as you want.

        <style name="AlertDialogFastStyling" parent="Base.Theme.AppCompat.Light.Dialog">
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
        <style name="AlertDialogFastStyling.Button" parent="Base.Widget.AppCompat.Button.ButtonBar.AlertDialog">
          	<item name="android:textColor">#009688</item>
          	<item name="android:textSize">14sp</item>
         </style>

  2. Apply your style (here is called `AlertDialogFastStyling`) to your `android.support.v7.app.AlertDialog` component. The following samples are available for testing and their insets show the visual mappings to `AlertDialogFastStyling`.

  2.1 Confirm Dialog
  
        AlertDialog dialog = new AlertDialog.Builder(context, R.style.AlertDialogFastStyling)
                        .setTitle("提醒")
                        .setPositiveButton("是", null)
                        .setNegativeButton("否", null)
                        .setMessage("检测到距离您上次清理已超过30天，是否立即清理？")
                        .show();
  
  ![confirm dialog](https://github.com/Cookizz/AlertDialog-Fast-Styling/blob/master/art/confirmdialog.png)
  
  ===
  2.2 Choice Dialog
  
        AlertDialog dialog = new AlertDialog.Builder(context, R.style.AlertDialogFastStyling)
                        .setItems(new String[]{"布丁味的老人茶", "奶昔", "巴拿拿牌烤香蕉"},
                                new DialogInterface.OnClickListener() {
                                    @Override
                                    public void onClick(DialogInterface dialog, int which) {
                                        dialog.cancel();
                                    }
                        })
                        .show();
                        
  ![confirm dialog](https://github.com/Cookizz/AlertDialog-Fast-Styling/blob/master/art/choicedialog.png)
  
  ===
  2.3 Radio Dialog
  
        AlertDialog dialog = new AlertDialog.Builder(context, R.style.AlertDialogFastStyling)
                        .setSingleChoiceItems(new String[]{"布丁味的老人茶", "奶昔", "巴拿拿牌烤香蕉"}, 0, null)
                        .setPositiveButton("确定", null)
                        .setNegativeButton("取消", null)
                        .show();
                        
  ![confirm dialog](https://github.com/Cookizz/AlertDialog-Fast-Styling/blob/master/art/radiodialog.png)
  
  ===
  2.4 Check Dialog
  
        AlertDialog dialog = new AlertDialog.Builder(context, R.style.AlertDialogFastStyling)
                        .setMultiChoiceItems(new String[]{"布丁味的老人茶", "奶昔", "巴拿拿牌烤香蕉"},
                                new boolean[] {false, true, true},
                                null)
                        .setPositiveButton("确定", null)
                        .setNegativeButton("取消", null)
                        .show();
                        
  ![confirm dialog](https://github.com/Cookizz/AlertDialog-Fast-Styling/blob/master/art/checkdialog.png)
  
