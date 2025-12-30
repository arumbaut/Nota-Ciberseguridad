Condicionale 
## Comparison Operators

- `-eq`: Equal to
- `-ne`: Not equal to
- `-lt`: Less than
- `-le`: Less than or equal to
- `-gt`: Greater than
- `-ge`: Greater than or equal to
## String Comparison Operators

- `=`: Equal to
- `!=`: Not equal to
- `<`: Less than, in ASCII alphabetical order
- `>`: Greater than, in ASCII alphabetical order
## Logical Operators

- `&&`: Logical AND
- `||`: Logical OR
- `!`: Logical NOT
## File Test Operators

- `-e`: Checks if a file exists
- `-d`: Checks if a directory exists
- `-f`: Checks if a file is a regular file
- `-s`: Checks if a file is not empty

```
El igual para los # es con las sentencias -eq, -ne, -lt, -gt
OPeradores ||, &

#Simple
if [ "$fruta" = "aranja"]; then

fi

#Compuesta
if [ "$fruta" = "aranja"]; then

else

fi

#Con elif
if [ "$fruta" = "aranja"]; then

elif [ "$fruta" = "aranja"]; then

else
fi
```

Instruccions case 
```
case "value" in
   m)codigo;;
   d)codigo;;
   C)codigo;;
esac
```