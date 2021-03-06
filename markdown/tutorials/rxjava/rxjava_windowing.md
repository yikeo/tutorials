# RxJava - Windowing
Windowing operator works similar to buffer operator but it allows to gather items emitted by an Observable into another observable instead of collection and emit those Observables instead of collections. In the example below, we've created an Observable to emit 9 items and using window operator, 3 Observable will be emitted together.

## Windowing Example
Create the following Java program using any editor of your choice in, say, C:\&gt; RxJava.

### ObservableTester.java
```
import io.reactivex.Observable;
import io.reactivex.Observer;
import io.reactivex.disposables.Disposable;
import io.reactivex.schedulers.Schedulers;

import java.util.concurrent.TimeUnit;

public class ObservableTester {
   public static void main(String[] args) throws InterruptedException {
      Observable<Integer> observable = Observable.just(1, 2, 3, 4,
         5, 6, 7, 8, 9);

      observable.subscribeOn(Schedulers.io())
         .delay(2, TimeUnit.SECONDS, Schedulers.io())
         .window(3)
         .subscribe(new Observer<Observable<Integer>>() {
            @Override
            public void onSubscribe(Disposable d) {
               System.out.println("Subscribed");
            }
            @Override
            public void onNext(Observable<Integer> integers) {
               System.out.println("onNext: ");
               integers.subscribe(value -> System.out.println(value));
            }
            @Override
            public void onError(Throwable e) {
               System.out.println("Error");
            }

            @Override
            public void onComplete() {
               System.out.println("Done! ");
            }
         });
      Thread.sleep(3000);
   }
}
```
### Verify the Result
Compile the class using **javac** compiler as follows −

```
C:\RxJava>javac ObservableTester.java
```
Now run the ObservableTester as follows −

```
C:\RxJava>java ObservableTester
```
It should produce the following output −

```
Subscribed
onNext: 
1
2
3
onNext: 
4
5
6
onNext: 
7
8
9
Done!
```

[Previous Page](../rxjava/rxjava_buffering.md) [Next Page](../rxjava/rxjava_quick_guide.md) 
