# ASM_bytecode_manipulation
Using ASM (a java lib) to manipulate java classes at run time


type safety


```
javac main.java
```


```
java -cp .;asm-all-5.0.3.jar org.objectweb.asm.util.ASMifier main
```

```
import java.util.*;
import org.objectweb.asm.*;
public class mainDump implements Opcodes {

public static byte[] dump () throws Exception {

ClassWriter cw = new ClassWriter(0);
FieldVisitor fv;
MethodVisitor mv;
AnnotationVisitor av0;

cw.visit(52, ACC_PUBLIC + ACC_SUPER, "main", null, "java/lang/Object", null);

{
mv = cw.visitMethod(ACC_PUBLIC, "<init>", "()V", null, null);
mv.visitCode();
mv.visitVarInsn(ALOAD, 0);
mv.visitMethodInsn(INVOKESPECIAL, "java/lang/Object", "<init>", "()V", false);
mv.visitInsn(RETURN);
mv.visitMaxs(1, 1);
mv.visitEnd();
}
{
mv = cw.visitMethod(ACC_PUBLIC + ACC_STATIC, "main", "([Ljava/lang/String;)V", null, null);
mv.visitCode();
mv.visitInsn(ICONST_2);
mv.visitInsn(ICONST_3);
mv.visitMethodInsn(INVOKESTATIC, "main", "add", "(II)V", false);
mv.visitInsn(RETURN);
mv.visitMaxs(2, 1);
mv.visitEnd();
}
{
mv = cw.visitMethod(ACC_PUBLIC + ACC_STATIC, "add", "(II)V", null, null);
mv.visitCode();
mv.visitFieldInsn(GETSTATIC, "java/lang/System", "out", "Ljava/io/PrintStream;");
mv.visitVarInsn(ILOAD, 0);
mv.visitVarInsn(ILOAD, 1);
mv.visitInsn(IADD);
mv.visitMethodInsn(INVOKEVIRTUAL, "java/io/PrintStream", "println", "(I)V", false);
mv.visitInsn(RETURN);
mv.visitMaxs(3, 2);
mv.visitEnd();
}
cw.visitEnd();

return cw.toByteArray();
}
}
```

or

```
java -cp .;asm-all-5.0.3.jar org.objectweb.asm.util.ASMifier main>mainDump.java
```
