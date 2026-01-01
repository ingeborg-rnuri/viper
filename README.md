# Aviso

Conteúdo produzido acompanhando um curso aberto. O material original não pertence a mim e não pode ser redistribuído.

---

Testes simples. Algumas observações que valem registrar:

- Um método abstrato declarado como protegido pode ser implementado como público na classe filha. O contrário não vale: não dá para reduzir a visibilidade que a classe pai definiu.
- Se a classe tem método abstrato, ela obrigatoriamente precisa ser abstrata.

Para as classes:

- `App.java`
```
public class App {
    public static void main(String[] args) throws Exception {
        Filho f = new Filho();
        f.protectedMethodOfFather();
        f.abstractPublicMethodOfFather();
        f.publicMethodOfFather();
        f.publicMethodOfChild();

        Pai g = new Filho(); 
        g.publicMethodOfFather();
        // Aqui não compila: a variável foi declarada como o tipo pai,
        // então só os métodos visíveis nesse tipo ficam acessíveis
    }
}
```
- `Father.java`:
```
abstract public class Pai {
    protected void protectedMethodOfFather() {
        System.out.println("Método protegido do pai");
    }
    abstract protected void abstractPublicMethodOfFather();

    public void publicMethodOfFather() {
        System.out.println("Método público do pai");
    }

    private void privateMethodOfFather() {
        System.out.println("Método privado do pai");
    }
}
```
- `Child.java`:
```
public class Filho extends Pai{
    public void publicMethodOfChild() {
        System.out.println("Método público do filho");
    }

    public void abstractPublicMethodOfFather() {
```