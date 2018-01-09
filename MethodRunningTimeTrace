import com.sun.btrace.annotations.*;
import static com.sun.btrace.BTraceUtils.*;

@BTrace
public class MethodRunningTimeTrace {
    @OnMethod(clazz = "me.huadi.ClassName", method = "methodName", location = @Location(Kind.RETURN))
    public static void traceExecute(@ProbeClassName String className, @ProbeMethodName String method, @Duration long time) {
        long durationTimeMilliSeconds = time / 1000000;
        if (durationTimeMilliSeconds > 0) {
            String output = className;
            output = strcat(output, "#");
            output = strcat(output, method);
            output = strcat(output, " - ");
            output = strcat(output, "[");
            output = strcat(output, str(threadId(currentThread())));
            output = strcat(output, "] ");
            output = strcat(output, "Running time: ");
            output = strcat(output, str(durationTimeMilliSeconds));
            output = strcat(output, " ms, ");
            output = strcat(output, "return line: ");
            output = strcat(output, str(probeLine()));
            output = strcat(output, ".");
            println(output);
        }
    }
}
