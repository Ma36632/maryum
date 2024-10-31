Submitted by:

Maryum Aftab

Roll no:

14658

Class:

BSCS 3A

Submitted to:

Sir Jamal Abdul Ahad

Subject:

DSA

Assignment 

1

Date:

8 October 2024

Department:

Computer science

University:

Abbottabad university of science and technology

Github link :  https://github.com/Ma36632/maryum

# Chapter 1

## The role of Algorithms in computing

### Exercises

#### Question 1

Describe your own real-world example that requires sorting. Describe one that requires finding the shortest distance between two points.

**Scenario**: Online Store Sorting Products by Price  
Imagine you are browsing an online store that sells electronics. The store allows you to sort products by price, either from lowest to highest or from highest to lowest. This is a classic use case for sorting, where you want to present the products in an organized way to help customers make better purchasing decisions.

**In this example**:  
**Sorting criteria**: Price (either ascending or descending)  
**Why sorting is important**: It helps users quickly find products within their budget or compare expensive and cheap products. This can be implemented using sorting algorithms like Merge Sort or Quick Sort for efficient sorting, especially when the number of products is large.

**Code**:
```python
def merge(arr, left_half, right_half):
    i = j = k = 0
    while i < len(left_half) and j < len(right_half):
        if left_half[i]['price'] < right_half[j]['price']:
            arr[k] = left_half[i]
            i += 1
        else:
            arr[k] = right_half[j]
            j += 1
        k += 1

    while i < len(left_half):
        arr[k] = left_half[i]
        i += 1
        k += 1

    while j < len(right_half):
        arr[k] = right_half[j]
        j += 1
        k += 1

def merge_sort(products):
    if len(products) > 1:
        mid = len(products) // 2
        left_half = products[:mid]
        right_half = products[mid:]
        merge_sort(left_half)
        merge_sort(right_half)
        merge(products, left_half, right_half)

if __name__ == "__main__":
    products = [
        {"name": "Laptop", "price": 999.99},
        {"name": "Smartphone", "price": 499.99},
        {"name": "Headphones", "price": 199.99},
        {"name": "Tablet", "price": 299.99}
    ]
    print("Original products:")
    for product in products:
        print(f"{product['name']} - ${product['price']}")
    merge_sort(products)
    print("\nSorted products by price (low to high):")
    for product in products:
        print(f"{product['name']} - ${product['price']}")
