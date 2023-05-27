# set
An implementation of the set type in golang.

## Example
	

	package main

	import "github.com/wdlea/set"

	const SET_SIZE uint64 = 1024
	
	type YourSetType struct{
		value uint64
	}
	
	func (t YourSetType) Hash(size uint64) uint64{ //define the Hash function to fulfil interface
		return t.value % size //the returned value MUST be less than the size parameter
	}

	func main(){
		s := set.MakeSet[YourSetType](SET_SIZE)//create a new set with the given type and size

		VALUE1 := YourSetType{
			value: 100,
		}
		
		//adds an item to the set
		s.Push(VALUE1)
	
		//Has and Pop return whether the item was in the set
		s.Has(VALUE1)//true

		//Pop removes the item
		s.Pop(VALUE1)//true

		//Meaning that any subsequent calls to either will return false
		s.Has(VALUE1)//false
		s.Pop(VALUE1)//false, note that this DOES NOT panic
		
	}