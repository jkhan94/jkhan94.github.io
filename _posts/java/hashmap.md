---
layout: post
title: Put multiple values in one key (Hashmap)
date: 2024-04-18
category: JAVA
---

## MapArray.java
```java
package json;

import java.util.HashMap;
import java.util.Iterator;
import java.util.LinkedList;
import java.util.Map;
import java.util.Map.Entry;
import java.util.Set;

public class MapArray {

	static class HashTest {
		int value1, value2, value3;
		String key;

		HashTest(String key, int a, int b, int c) {
			this.key = key;
			this.value1 = a;
			this.value2 = b;
			this.value3 = c;
		}
	}

	public static void main(String[] args) {
		// 1-1. 2차원 배열 생성
		String valueArr[][] = { { "value1_1", "value1_2", "value1_3" }, { "value2_1", "value2_2", "value2_3" },
				{ "value3_1", "value3_2", "value3_3" } };

		// 1-2. Map에 배열 넣기
		Map<Integer, String[]> arrMap = new HashMap<>();
		arrMap.put(1, valueArr[0]);
		arrMap.put(2, valueArr[1]);
		arrMap.put(3, valueArr[2]);

		// 키-값 쌍
		System.out.println("Entry");
		Set<Entry<Integer, String[]>> items = arrMap.entrySet();
		for (Entry<Integer, String[]> entry : items) {
			System.out.print(entry + "\n");
		}
		System.out.println();

		// 키만 뽑을 경우 keySet() -> iterator()
		System.out.println("keySet");
//		System.out.println(arrMap.keySet());
		Iterator<Integer> iter = arrMap.keySet().iterator();
		while (iter.hasNext()) {
			System.out.print(iter.next() + "\n");
		}
		System.out.println();

		// 값만 뽑을 경우 values() -> iterator()
		System.out.println("values");
//		System.out.println(arrMap.values());
		Iterator<String[]> iter1 = arrMap.values().iterator();
		while (iter1.hasNext()) {
			System.out.print(iter1.next() + "\n");
		}
		System.out.println();

		///////////////////////////////////////////
		// 2-1. Map에 List 넣기
		LinkedList<String> valueList = new LinkedList<>();
		valueList.add("AAA");
		valueList.add("BBB");
		valueList.add("CCC");

		// 2-2. Map에 List 넣기
		Map<String, LinkedList<String>> listMap = new HashMap<>();
		listMap.put("key01", valueList);

		System.out.println("LinkedList");
		Set<Entry<String, LinkedList<String>>> item = listMap.entrySet();
		for (Entry<String, LinkedList<String>> entry : item) {
			System.out.print(entry + "\n");
		}
		System.out.println();

		////////////////////////////////////////////////
		// 3. 클래스로 선언해서 배열 넣기
		Map<String, HashTest> mHashTest = new HashMap<>();
		HashTest hashTest = new HashTest("testKey", 10, 20, 30);
		mHashTest.put("testKey", hashTest);

		System.out.println("Class");
		for (String key : mHashTest.keySet()) {
			System.out.println("Result : " + key + ", " + mHashTest.get(key).value1 + ", " + mHashTest.get(key).value2
					+ ", " + mHashTest.get(key).value3);
		}

	}

}
```
```console
Entry
1=[Ljava.lang.String;@626b2d4a
2=[Ljava.lang.String;@5e91993f
3=[Ljava.lang.String;@1c4af82c

keySet
1
2
3

values
[Ljava.lang.String;@626b2d4a
[Ljava.lang.String;@5e91993f
[Ljava.lang.String;@1c4af82c

LinkedList
key01=[AAA, BBB, CCC]

Class
Result : testKey, 10, 20, 30

```
