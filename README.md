# Android_ClipBoardManager
Playing with clip board

# Code

#### 1st Activity 
```
Button copyButton, pasteButton;
TextInputLayout editText;

ClipboardManager clipboardManager;

copyButton = findViewById(R.id.copyButton);
pasteButton = findViewById(R.id.pasteButton);
editText = findViewById(R.id.input_layout);

clipboardManager = (ClipboardManager) getSystemService(Context.CLIPBOARD_SERVICE);

    copyButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                try {
                    String toBeCopied = editText.getEditText().getText().toString();
                    if (!toBeCopied.equals("")) {

                        ClipData clipData = ClipData.newPlainText("dataFromEditText", toBeCopied);
                        clipboardManager.setPrimaryClip(clipData);

                        Toast.makeText(MainActivity.this, "Copied To clipboard", Toast.LENGTH_SHORT).show();
                        editText.getEditText().setText(""); //delete the entered data

                    } else
                        Toast.makeText(MainActivity.this, "Please Enter Some Text", Toast.LENGTH_SHORT).show();
                } catch (Exception e) {
                    Toast.makeText(MainActivity.this, "Your Clip Board is empty", Toast.LENGTH_SHORT).show();
                }
            }
        });
        
        pasteButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                ClipData.Item item = clipboardManager.getPrimaryClip().getItemAt(0);
                String toBePasted = item.getText().toString();

                if (!toBePasted.equals("")) {

                    editText.getEditText().setText(toBePasted);
                    Toast.makeText(MainActivity.this, "Pasted Recent Copy From Clipboard", Toast.LENGTH_SHORT).show();

                } else
                    Toast.makeText(MainActivity.this, "Clipboard Empty", Toast.LENGTH_SHORT).show();
            }
        });

```

# App Highlight

<img src="app_images/Copy Paste Code.png" width="1000" /><br>

<img src="app_images/Copy Paste App1.png" width="300" /> <img src="app_images/Copy Paste App2.png" width="300" /> <img src="app_images/Copy Paste App3.png" width="300" /><br>
