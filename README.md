# Portfolio-Final-

Here is the Java source code for the fianl project.

public class CounterApp}

private static volatile boolean countingComplete = false;

    public static void main(String[] args) {
        Thread counterUp = new Thread(new CounterUp());
        Thread counterDown = new Thread(new CounterDown());

        counterUp.start();
        try {
            counterUp.join(); // Wait for counterUp to finish
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        
        countingComplete = true; // Notify that the counting up is complete
        counterDown.start(); // Start the countdown
    }

    static class CounterUp implements Runnable {
        public void run() {
            for (int i = 1; i <= 20; i++) {
                System.out.println("Count Up: " + i);
                try {
                    Thread.sleep(500); // Simulate work
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        }
    }

    static class CounterDown implements Runnable {
        public void run() {
            while (!countingComplete) {
                // Wait for counting complete
            }
            for (int i = 20; i >= 0; i--) {
                System.out.println("Count Down: " + i);
                try {
                    Thread.sleep(500); // Simulate work
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}
