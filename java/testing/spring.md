# Spring Testing

## Verify log message

Useful in error scenarios to verify that the details are being correctly logged.

* Add ```@ExtendWith(OutputCaptureExtension.class)``` to the Class
* Add ```CapturedOutput output``` as a parameter to the test method
* Use ```output.getOut().contains("String")``` to verify whether the logs contain the specified message

E.g.
```
import org.junit.jupiter.api.Assertions;
import org.junit.jupiter.api.Test;
import org.junit.jupiter.api.extension.ExtendWith;
import org.springframework.boot.test.system.CapturedOutput;
import org.springframework.boot.test.system.OutputCaptureExtension;

@ExtendWith(OutputCaptureExtension.class)
class OutputCaptureTest {
    @Test
    void outputCaptureTest(CapturedOutput output) {
        System.out.println("Some test string");
        Assertions.assertTrue(output.getOut().contains("test string"));
    }
}
```