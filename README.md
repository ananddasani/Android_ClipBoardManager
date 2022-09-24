# Android_ClipBoardManager
Playing with clip board

This topic is a part of [My Complete Andorid Course](https://github.com/ananddasani/Android_Apps)

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

![Copy Paste Code](https://user-images.githubusercontent.com/74413402/192094922-5f400fc4-cbf4-4c5b-838e-8a397a0b8c6e.png)
![Copy Paste App1](https://user-images.githubusercontent.com/74413402/192094927-410a8115-19c2-4542-aabf-20a4dca12fc4.png)
![Copy Paste App2](https://user-images.githubusercontent.com/74413402/192094934-50184072-52fc-482c-850f-302e7c51a151.png)
![Copy Paste App3](https://user-images.githubusercontent.com/74413402/192094936-8073efed-cd8b-46d8-8a6c-d6b07bca6886.png)

