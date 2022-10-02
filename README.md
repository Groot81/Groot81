- 👋 Hi, I’m @Groot81
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Groot81/Groot81 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
React Component Code Review
 ----> Based on the code below answer the following queries:
 1 .Explain what the simple List component does. 
ANS ----> ⦿ A list is used to store multiple items of the same and different datatype under a variable.
 It is basically an array. We can perform various operations on it such as .map() to loop over the list/array to list down all the elements.
 There is also a memo method used in the list component. 
React reuses the memoized content from the same reference. 
It makes the website speed and performance more efficient and better.
 ⦿ Simple list component accepts various props and renders a list item on the page and background color of list item is determined by isSelected prop.
 If item is selected then background color of item is green else background color is red by default. 

2 .What problems / warnings are there with code?
 ANS-----> In list item's onClick method there is a function call but onClick accepts function's reference.

 ⦿ CODE
 
<li style={{ backgroundColor: isSelected ? 
"green" : "red" }} 
   onClick={onClickHandler(index)}>
    {text}
</li> Syntatical error in returned value of useState()

 ⦿ CODE 
    const [setSelectedIndex, selectedIndex] = useState(); 
  Passing incorrect propType value in isSelected.
  Proptype defined is bool but here passed proptype is number 
⦿ CODE 
<ul style={{ textAlign: "left" }}> 
    {items.map((item, index) => ( 
    <SingleListItem 
     onClickHandler={() => handleClick(index)} 
     text={item.text} 
     index={index} 
     isSelected={selectedIndex}  
     /> 
     ))} 
</ul> 
      Items Array is null and iterating over null array is not possible or may cause run-time error 
⦿ CODE 
WrappedListComponent.defaultProps = { 
  items: null, 
}; 
      Syntatical error in following code 
⦿ CODE 
  WrappedListComponent.propTypes = { 
items: PropTypes.array( 
 PropTypes.shapeOf({ 
 text: PropTypes.string.isRequired, 
  }) ),
 };
  
    Key prop is not present for uniquely identify each element
 ⦿ CODE 
 <ul style={{ textAlign: 'left' }}> {
    items.map((item, index) => ( 
    <SingleListItem 
    onClickHandler={() => handleClick(index)} 
    text={item.text} 
    index={index} 
    isSelected={selectedIndex} 
    /> 
   ))}
