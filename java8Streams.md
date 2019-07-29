# Quick examples of Java 8 Streams

## Integer Streams




## String Streams

        Stream.of("Ava", "Anero", "Alberto")
              .sorted()
              .findFirst()
              .ifPresent(System.out::println);
              
## String Streams              
              
              
              String [] names = {"Al", "Ankit", "Kushal", "Brent", "Sarika", "Amanda", "Hans", "Sean", "Joe", "Barry", "Greg"};
        Arrays.stream(names)
                .filter(x -> x.startsWith("S"))
                .sorted()
                .forEach(System.out::println);
