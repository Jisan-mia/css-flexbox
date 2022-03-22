## CSS FLEXBOX


**What's this?**
Flexbox is a css box model to easily layout, align and distribute space among items withing a container either horizontally or vertically.

**What Flexbox can do for us?**
   - Simplify layouts
   - Reduce need for media queries(responsive design)

## Topics Covered
| Flex container properties | Flex items properties |
| :---- | :---- |
| `display` | `align-self` |
| `flex-direction` | `order` |
| `flex-wrap` | `flex-grow` |
| `flex-flow` | `flex-shrink` |
| `justify-content` | `flex-basis` |
| `align-items` | `flex` |
| `align-content` |  


### Note
| If your think you feel more comfortable reading Bangla explanation here is my another article **[Learn CSS Flexbox in an interesting way!](https://jisanmia.medium.com/learn-css-flexbox-in-an-interesting-way-3ed3c826efb9)** explained in Bangla |
| --- |


## Before get started we need to know some of the flexbox basics:

- In flexbox, the element or container which wraps all the children elements or items is called _flexbox container_ and childrens or each children elements/items are called _flexbox items_.
- Flex container has their own properties and values
- Same goes to children, also flex items/childrens has their own properties and values
- In flexbox, there are two axis, they are _Main axis_ and _Cross axis_.
- To make a flex container `display: flex;`
- By default, `flex-direction` is row. We can change the flex-direction to
  
  ```css
  flex-direction: row || row-reverse || column || column-reverse
  ```
- When `flex-direction: column || column reverse` one thing happens here, _main axis_ come into the place of _cross axis_ and _cross axis_ take place of _main axis_


![flexbox](images/flex.png "Image Title")


## Available properties for Flex container

- Obviously, to make a container flex container we need to write `display: flex`
- To change the directions of flex items there is-

  ```css
  flex-direction: row || row-reverse || column || column-reverse
  ```

- `flex-wrap: wrap;` makes its container to wrap all its items inside the container and the overflow items take place in a new line.
   - by default, _`flex-wrap: nowwrap;`_ overflows the container
   - _`flex-wrap: wrap-reverse`_ wrap in reverse way

- There is another property which control the items flow by combining _flex-direction_ and _flex-wrap_ property values. Eg.
   - `flex-flow: row-reverse wrap;`


### Main axis alignment properties

---

- _`justify-content`_ property defines how the remaining space of content of main-axis should be distributed in main-axis.
   - _`justify-content: flex-start (default)`_ move/align the content to the start
   - _`justify-content: flex-end `_ move/align the content to the end
   - _`justify-content: center`_ move/align the content in the center
   - _`justify-content: space-around`_ space around each items equally from the remaining space
   - _`justify-content: space-between`_ give space between every items
   - _`justify-content: space-evenly`_ space equally in every items


### Cross axis alignment properties

---

- _`align-items`_ property defines how the remaining space of items(alignment content) of cross axis should be distributed in cross axis.
   - _`align-items: stretch`_ default
   - _`align-items: flex-start`_ align items to the start
   - _`align-items: flex-end`_ align items to the end
   - _`align-items: center`_ align items to the center
  
- _`align-content`_ property defines how the remaining space of the full content should be distributed in cross axis. 
> If `flex-wrap` value is set to anything other than `nowrap`, only then we have to use `align-content` in the place of `align-items`. And it has the same possible values as `align-items`
  
   - _`align-content: flex-start`_ default. align content to the start in cross-axis
   - _`align-content: flex-end`_ align content to the end
   - _`align-content: center`_ align content to the center
   - _`align-content: space-around`_ space around each items equally from the remaining space
   - _`align-content: space-between`_ equal space between items
  - _`align-content: space-evenly`_ equal space around items


## Also there are some properties for flex items/children. Let's explore them

- _`align-self`_ property used to align individual flex items. Essentially it's the same exact thing as `align-items` except it only applies to a single flex item.
  - _`align-self: flex-start`_ (default) align single item to the start of the container
  - _`align-self: flex-end`_ (default) align single item to the end
  - _`align-self: center`_ (default) align single item to the center of the container
   
- _`order`_ property defines its/items order or sequences. Values of order property must be an integer
   - _`order: 0`_ (default) by default each items has the value 0
   - _`order: 1 | 2 | 3 | etc.`_ Item orders from the lowest order number to the largest order number.
  
- _`flex-grow`_ property of a flex item defines how items should grow (চউরা হবে). It's going to apply to flex-items when they don't naturally fill the entire main axis of the container.
   - _`flex-grow: 0`_ means by default each-items/item is going to take up 0 percent of the empty space within the container
   - _`flex-grow: 1`_ each-items/item grows equally to fit the container width or take up empty space in main-axis. 
   - _`flex-grow: 3`_
   
<pre>

flex-grow in detail:

imagine we have a 300px width container and
it has 4 items with 30px width and 30px height

4 items total width, 30X4 = 120x, 
remaining empty space, 300-120x = 180px 

first 3 item `flex-grow` value is set to 1 and the last item `flex-grow: 3`
sums up, 1+1+1+3 = 6 unit

Now, we have to divide 180/6 = 30px
means, 1 unit = 30px

.item-1,{
   flex-grow: 1 (total width, 30px + 1X30 = 60px)
}
.item-2{
   flex-grow: 1 (total width, 30px + 1X30 = 60px)
}
.item-3{
   flex-grow: 1 (total width, 30px + 1X30 = 60px)
}
.item-4{
   flex-grow: 3 (total width, 30px + 4X30 = 120px)
}

All-total width, 
60+60+60+120 = 300px which is equals to container width.

That's how flex-grow property actually works

</pre>

- _`flex-shrink`_ property defines if items should shrink or not or ছোট হবে কি হবে না তা ডিফাইন করে। It's the opposite of `flex-grow` which defines whether flex-items will fil up the empty space of it's container. On the other hand, `flex-shrink` controls the overflow the flex-items.
   - _`flex-shrink: 1`_ default. means means items will shrink to fit into the container width
   - _`flex-shrink; 0`_ means it won't shrink

<pre>

flex-shrink in detail:

imagine we have a 400px width container and it's items dimension is 50px/50px.

8 flex-items(8*50 = 400) will fit perfectly in that container(400px)

Now, instead of 8 item we added 9 flex-items. it overflow the container, because total flex-items width(9*50 = 450px) is getter than container width(400px). So it overflows by 50px(450px-400px). 

This will fit within the container, because by default all flex-items have `flex-shrink: 1`. It means that if we overflow by 50px, each flex item will take an equal share of that overflow and shrink by that amount (so long as it doesn't shrink the items less than the size of their content).

# Breaking it down:
  - 400px total width
  - 9 flex-items at a width of 50px each = 450x, so there is 50px overflow(450-400)
  - each flex item: `flex-shrink:1`
  - 9 flex item, so add `flex-shrink` values, we get, 1+1+1+1+1+1+1+1+1 = 9 units
  - 50px of overflow / 9 units = 5.55px
  - so, each item will reduce from an original size of 50px to a size of 50px-5.55px = 44.45px
  - now each flex-items should have 44.45 px width

Each flex item can only shrink so far. Eventually, it reaches its smallest possible width, which is the width of its inner content.

---

=> Here is an another scenario in `flex-shrink`
Now let's add 12 flex-items instead of 9. it overflows but items(10,11,13) does not fit into the container.

\
# Let's break it down again
   - 400px
   - 12 flex items, each has 50px width, total, 50*12 = 600px, so there is a overflow of 200px(600px-400px)
   - each items `flex-shrink:1`
   - 12 items `flex-shrink` value sums up to, 1+1+1+1+1+1+1+1+1+1+1+1 = 12 unit
   - 200px of overflow / 12 unit = 16.66px
   - so each item will reduce from an original size of 50px to a size of 50px - 16.66px = 33.34px

Sounds great, but the problem is items(10,11, 12) cannot shrink to 33.34px,which means we are going to have some overflow. 
Remember, flex items can shrink, but not more than their inner content


---

Now, let's see how we can use `flex-shrink` to define how our overflow space is allocated to flex-item. For this we'll add 9 flex-item within the container, since we know it'll fit into the container perfectly with a overflow of 5opx(50px flex items*9 = 450px-400px of total flex-container). At that moment each flex-item has `flex-shrink:1` which means they'll receive an equal allocation (so long as that doesn't shrink the item smaller than its content).

What if I wanted the first 3 items to keep their full size of 50px and let the remaining items absorb that 50px overflow. we can do it by setting pu `flex-shrink` value to 0.

.container {
  display: flex;
}
.child-1{
  flex-shrink: 0; 
}
.child-2 {
  flex-shrink: 0; 
}
.child-3 {
  flex-shrink: 0; 
}


# Now if we calculate, what'd be the reduced size of flex-items.
   - 0 + 0 + 0 + 1 + 1 + 1 + 1 + 1 + 1 = 6 unit
   - Total overflow of 50px (50px * 9 = 450px - 400px = 50px)
   - 1 unit = 50 / 6 = 8.34px
So in this scenario flex-item 1,2,3 keep their original size of 50px and remainder are reduced 8.34px


</pre>

- _`flex-basis`_ alternative of _`min-width`_ property in flexbox layout. We use _`flex-basis`_ for responsiveness.
   - _`flex-basis: 33.33%`_ you know how to set width in css

- And lastly but not least there is another property which combines _`flex-grow`_, _`flex-shrink`_ and _`flex-basis`_ into one property and should be written there values separated by spaces. The property name is _`flex`_
   - _`flex: 1 1 33.33%`_ flex-grow value | flex-shrink value | flex-basis value


---

## Let's create national flag of Bangladesh using css flexbox
 ![flag](images/flag.png)

It won't take more than just 2 minute to create the flag. I'll show you step by step

1. HTML part: create html boilerplate code by typing ! and hit tab on vscode. 

2. Inside body tag
   ```html
   <div class="rectangle">
      <div class="circle"></div>
   </div>
   ```
3. Inside head tag
   ```css
   .rectangle{
      background-color: #00684D;
      width: 500px;
      height: 300px;
      border-radius: 5px;
      margin: 0 auto;
      
      /* this flex-box code do the main part */
      display: flex;
      justify-content: center;
      align-items:  center;
   }
   .circle{
      width: 220px;
      height: 220px;
      margin-right: 45px;
      border-radius: 50%;
      background-color: #E72D41;
   }
   ```
### I know you got your expected output at the same time now you understand what's happening on the code. If not then try reading it carefully again.
### Okay, if you think this _hijibiji_ English is not understandable to you then Guess What! [Learn With Sumit](https://www.youtube.com/c/LearnwithSumit) has a wonderful course on CSS FLEXBOX in bangla where I also got clarified about this topic. The course is available for completely free both on [youtube](https://www.youtube.com/watch?v=kRS5ficucNM) and [udemy](https://www.udemy.com/course/css-flexbox-crash-course-in-bangla/)  about css flexbox
