# ASM_bytecode_manipulation
Using ASM (a java lib) to manipulate java classes at run time



How to run ASMifier to transforms a class file into the source code that would generate that class using ASM's APIs.

How to Asmify your class. Its simple:

Compile your class:

```
javac main.java
```

*There are 2 ways, either to output code in cmd or in a file:

1. Use ASMifier from the jar to load the source code: (Command for windows, for linux use ':' in place of ';')

```
java -cp .;asm-all-5.0.3.jar org.objectweb.asm.util.ASMifier main
```

Voilà you have the code:

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

2. Save the code in a file mainDump.Java:

```
java -cp .;asm-all-5.0.3.jar org.objectweb.asm.util.ASMifier main>mainDump.java
```
