- To remove all null's from a collection:

 	c.removeAll(Collections.singleton(null));

- To add multiple values to already initialized list:

 	list.addAll(Arrays.asList(a, b, c, d, e, f, g));

- To add multiple values to a not yet initialized list:

 	List<E> list = new ArrayList<E>(Arrays.asList(a, b, c, d, e, f, g));

- To iterate over the keys in a Map:

	for (KeyType key: map.keySet()){
		System.out.println(key);
	}

- To iterate over the keys in a Map with an iterator:

	Iterator<KeyType> it = map.keySet().iterator();

	while (it.hasNext()) {
		System.out.println(it.next());
	}

- To iterate over key-value pairs in a Map:

	for (Map.Entry<KeyType, ValueType> el: map.entrySet()) {
		System.out.println(el.getKey() + ": " + el.getValue());
	}

- To sort Map by Keys (using TreeMap, which is slower than HashMap because it runs sorting operation with each insertion, update and removal):

	Map<K,V> sortedMap = new TreeMap<K,V>(map);

- To sort Map by Keys (LinkedHashMap will keep the keys in the order they are inserted):

	List<K> keys = new ArrayList<K>(map.keySet());
	Collections.sort(keys);
	Map<K,V> sortedMap = new LinkedHashMap<K,V>();
	for(K key: keys){
		sortedMap.put(key, map.get(key));
	}

- To sort Map by Values:

	List<Map.Entry<K,V>> entries = new LinkedList<Map.Entry<K,V>>(map.entrySet());
	Collections.sort(entries, new Comparator<Map.Entry<K,V>>() {
		@Override
		public int compare(Entry<K, V> o1, Entry<K, V> o2) {
			return o1.getValue().compareTo(o2.getValue());
		}
	});
	Map<K,V> sortedMap = new LinkedHashMap<K,V>();
	for(Map.Entry<K,V> entry: entries){
		sortedMap.put(entry.getKey(), entry.getValue());
	}

- String concatenation:

	a += b is the equivalent of
	a = new StringBuilder().append(a).append(b).toString();

- Method Overloading vs. Overriding:

	Method Overloading: method with same name co-exists in same class, but they must have different method signatures. Resolved using static binding at compile time.

	Method Overriding: method with same name and same signature is declared in derived class or sub-class. Resolved using dynamic binding at runtime. Examples: equals(), hashCode(), compareTo(). Cannot override static methods (main(), for example) because they are associated with Class rather than object, and resolved and bonded during compile time. Also, private and final methods cannot be overridden. Good practice is to use @Override annotation.








 	