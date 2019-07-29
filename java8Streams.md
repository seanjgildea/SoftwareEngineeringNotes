# Quick examples of Java 8 Streams

## Average of squares of int array

      Arrays.stream(new int[] {2, 4, 6, 8, 10})
                .map(x -> x * x)
                .average()
                .ifPresent(System.out::println);

## Stream.of, sorted and findFirst

        Stream.of("Ava", "Anero", "Alberto")
              .sorted()
              .findFirst()
              .ifPresent(System.out::println);
              
## Stream from Array, sort, filter and print
              
              String [] names = {"Al", "Ankit", "Kushal", "Brent", "Sarika", "Amanda", "Hans", "Sean", "Joe", "Barry", "Greg"};
        Arrays.stream(names)
                .filter(x -> x.startsWith("S"))
                .sorted()
                .forEach(System.out::println);


## Stream List of names sorted, convert them to lowercase, filter by length and print

                List<String> people1 = Arrays.asList("Al", "Ankit", "Kushal", "Brent", "Sarika", "Amanda", "Hans", "Sean", "Joe", "Barry", "Greg");
        people1
                .stream()
                .map(String::toLowerCase)
                .filter(x -> x.length() > 4)
                .forEach(System.out::println);
