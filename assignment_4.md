### 1. Given a string “Azad Ram Madiha Yash”. Return a string with the first letter of every word from the string. (Use built in methods).

```
let myString = "Azad Ram Madiha Yash";
let words = myString.split(" ");
let newString = words.map(word => word[0]).join("");
console.log(newString);
```

### 2. Given an array [1, -4, 12, 0, -3, 29, -150]. Calculate the sum of all positive numbers (use built in array methods).

```
 var arr = [1, -4, 12, 0, -3, 29, -150];
 var sum = arr.reduce((total,x)=>{
     if(x>0)
     return total+x;
     else
     return total;
     },0);
console.log(sum);
```

### 3. Given an array [1, 2, 3, 4, 5]. Create a new array with the square of each element(use built in array methods).

```
var a=[1,2,3,4,5];
var b = arr.map(x=>x**2);
console.log(b);
```

## 4. Given an array [{ id: 2100, name: 'President Jacqueline' }, { id: 2114, name: 'Vice-president James' }, { id: 3016, name: 'House-captain Otis' }, { id: 4818, name: 'Prefect Finneas' }]. Create an array containing just the id of every individual. (write two solution one using iterator and another using built-in method)

Using iterator :

```
var a= [{ id: 2100, name: 'President Jacqueline' }, { id: 2114, name: 'Vice-president James' }, { id: 3016, name: 'House-captain Otis' }, { id: 4818, name: 'Prefect Finneas' }];
var idList=[];
for(var i=0;i<a.length;i++){
    idList.push(a[i].id);
}
console.log(idList);
```

Using inbuilt method:

```
var a= [{ id: 2100, name: 'President Jacqueline' }, { id: 2114, name: 'Vice-president James' }, { id: 3016, name: 'House-captain Otis' }, { id: 4818, name: 'Prefect Finneas' }];
var idList=a.map(x=>x.id);
console.log(idList);
```
