## Singletion模式
- 所谓单例模式，就是这个类只能创建一个唯一的对象，当需要这样逻辑的时候，就可以用单例模式保证只会生成一个对象，不会因为误操作出现潜在的逻辑错误。
- 在cpp中，单例模式的实现就是将构造函数作用域放入私有中，这样构造函数无法被外部访问，然后再类内部创造一个public的static对象并提供一个静态成员函数来访问这个对象。这个静态成员函数就是值返回这个对象。
- 根据这个静态对象生成的位置，有所谓懒汉模式与饿汉模式。
- - 饿汉模式就是说，我一开始不创建这个对象，只在第一次访问的时候创建，这样就直接在类中构造一个对象即可。这样的好处是一定线程安全，因为类中静态的对象只会构造一次。但我觉得这两个差别不大，都是静态对象了，这样只是在保证不new两次，但是访问这个对象时还是不安全，最安全的办法只有**加锁**。
- - 懒汉模式就是说，只有在第一次调用的时候才会new一个对象出来，这样的话，如果多个线程同时调用getInstance时，可能会出现多次new的一个情况，可能会导致一些逻辑错误与内存泄露，所以如果懒汉模式想要对象创建时保证线程安全，就得加锁。
