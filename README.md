
# Rapport

För denna uppgift så behövdes en SecondActivity skapas som ska nås via MainActivity. 
Jag valde att skapa två knappar. En i varje aktivitet som tar en mellan de två aktiviteterna.
I filen activity_second.xml skapades en Edittext med ett id som används för att tilldela variabeln 
preferences värdet av vad användaren skriver in i textfältet. 
I activity_main skapade jag en textview som ska ta emot användarens input och visa upp den på skärmen.


Koden som visas i figur 1 kommer från filen SecondActivity.java. Den redovisar hur jag har gjort för att användarens input ska sparas när man trycker på knappen.
Figur 1 Kod
```
   SharedPreferences preferences;
   ...
   protected void onCreate(Bundle savedInstanceState) {
     input = findViewById(R.id.input);
     preferences = getSharedPreferences("preferences", MODE_PRIVATE);

        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(SecondActivity.this, MainActivity.class);
                SharedPreferences.Editor editor = preferences.edit();
                editor.putString("name", input.getText().toString());
                editor.apply();
                startActivity(intent);
            }
        });
```


När man återgår till första skärmen så ska användarens input visas upp i en textview.
Detta görs genom att i filen MainActivity.java hämta SharedPreferences och lägga in den i en strängvariabel som sen kan skrivas ut i textview. 
Figur 2 Kod
```
   protected void onResume() {
        super.onResume();

        preferences = getSharedPreferences("preferences", MODE_PRIVATE);
        String name = preferences.getString("name", "inget namn hittades");
        textviewname.setText(name);

    }
```


Denna bild är från andra skärmen (second activity), där användaren kan skriva in önskat ord.
![](second.png)

Användarens input visas sen upp när hen har tryckt på knappen och i bilden nedan syns det hur inputen visas upp på första skärmen (main activity).
![](main.png)
