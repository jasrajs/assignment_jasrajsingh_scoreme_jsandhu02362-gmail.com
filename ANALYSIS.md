//TASK 2 
1 - ConcurrentModificationException occurs when a collection (like ArrayList) is structurally modified while it is being iterated using an iterator or enhanced for-loop except for the iterator's own methods for this approach .

2- The code pattern that might have triggered this error at line 142 could be this where we are trying to alter the orginal list (transactions as in the example given below) whole itterating it :-
for (Transaction tx : transactions) {
transactions.remove(tx);
}
Or
transactions.forEach(tx -> {
if (somefiltercondition) {
transactions.remove(tx);
}
});

3- To solve it you can use iterator’s own remove:-
Iterator itr = transactions.iterator();

while (itr.hasNext()) {
Transaction tx = itr.next();

if (condition) {
itr.remove();
}
}
In this way we can avoid getting a ConcurrentModificationException as we are not direclty altering the original list .
