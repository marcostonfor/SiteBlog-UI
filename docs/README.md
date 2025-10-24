# SiteBlog-UI

Software escrito en typescript que genera interfaces de usuario. Front-End
generator. Es imprescindible utilízar `typescript` para usarlo y el uso del
paradigma de programacíon orientado a objetos, ya que el codigo base o core es
100% clases y orientado a objetos.

> En resumen:\
> Este software, `SiteBlog-UI` en principío solo interesa a desarrolladores en
> `typescript` que quíeran desarrollar un front-end, orientado a objetos y hábil
> por si mismo. Por hábil entíendo capaz de ser dinámico tambíen."`nadíe díjo`
> que el resultado de usar `SiteBlog-UI` tenga que ser estático" aúnque ahora
> mísmo es lo que es el resultado una web estática sin más.

## ¿Qué és?

> ### `SiteBlog-UI` es un simple software capaz de generar interfaces de usuario y gracias a la magia de `webpack` lo que define es un front-end completo o `site`, `blog`, `web` tal front-end que queda configurado como un `sitio estático`

## ¿Cómo se úsa?

> ### La forma idónea u optíma de usar `SiteBlog-UI` -en adelante este software- depende de lo que decída el desarrollador crear y cómo estructura el código de lo nque este desarrollando, -síempre un front-end "por lo menos de momento"-.

Está/s forma/s de instánciar o usar el core o código base de este software, es
algo en definicíon todavía, es decír lo estoy probando aún. Sin embargo el
proceso requíere bíen `crear clases` bíen `instánciar clases`.\
Explicańdolo:

1. opcíon `crear clases`
   - Core = clases y tipos.\
     mi código, el que genero\
     tambíen son clases. En ú_\
     ltima instáncia la invoc_\
     acíon se hace mediante la\
     llamada al metodo que en_\
     capsula un contenído dado\
     por la clase que hemos cr_\
     eado.
2. opcíon `instánciar clases`
   - Core = clases y tipos.\
     mi código, el que genero\
     son instáncias de estás\
     clases, y del mísmo modo\
     se úsan llamando al metodo\
     que crea el contenído.
3. Ejemplos:

```typescript
// Ejemplo con la creacíon de
// un header que usa una clase
// para generar contenído

export class FirstSection extends Section {
    constructor() {
        super();
    }

    public firstColumn() {
        const container = new Div();
        const encabezado = new H1();
        const logoimage = new Img();
        const logo = new Figure();
        logoimage.setImg("./assets/img/rocketride.png", "logo", {});
        encabezado.setContent("SiteBlog-UI");
        logo.setFigcaption(encabezado.getHeading());
        logo.appendContent(logoimage.getImg());
        container.setContent(logo.getFigure());
        return this.appendContent(container.getDiv());
    }
    /**
     * Aquí
     */
    // Más metodos o seccíones
    // para la 1ª seccíon del
    // header.
}
```

```typescript
// Creacíon e insercíon del header

const firstSection = new FirstSection();

export function header() {
    const header = new Header();
    header.appendContent(firstSection.firstColumn());
    document.addEventListener("DOMContentLoaded", () => {
        CreateElement.setElement(header.getHeader(), "ofRender"); // ofRender es un id que debe existír en el index.html y que es dónde va a incluírse el contenído del metodo al invocarlo. Obvía decír que es un id aleatorío y que debe escribirse con la redaccíon del metodo que genera un header con contenido.
    });
}
```

```typescript
// Sin crear clases, es decír;
// instánciando las clases que
// componen el código fuente base.

/**
 * Este código de abajo representa
 * la generacíon de un simple for_
 * mulario de acceso.
 */

const encabezado = new H2();
encabezado.setAttributes({ id: "tituloFormularioLogin" });
encabezado.setContent("Acceder");
const iconTitle = new InlineContainer();
const icon = `<strong class="icons">&#x1f679;</strong>`;
let render = document.createElement("i");
render.innerHTML = icon;
encabezado.setContent(render);
iconTitle.setContainerHelper(encabezado.getHeading());

const inputName = new Input();
inputName.setType({ text: "text" });
const inputPassword = new Input();
inputPassword.setType({ password: "password" });

const iconCheck = new InlineContainer();
const iconChck = `<i class="icons iconCheck">&#x1f5f6;</i>`;
iconCheck.setContainer(iconChck);
const check = new Input();
check.setType({ checkbox: "checkbox" });
const checkLabel = new Label();
checkLabel.appendContent(iconCheck.getContainer());
checkLabel.setLabel("Recordarme", "persistbtn");

const lname = new Label();
lname.setLabel("Nombre de usuario:", "user");
const lpassword = new Label();
lpassword.setLabel("Clave de acceso.", "contrasenya");

const iconName = new InlineContainer();
const icon2 = `<strong class="icons">&#x1f610;</strong>`;
const render2 = document.createElement("i");
render2.innerHTML = icon2;
iconName.setContainerHelp(lname.getLabel(), render2);

const inputsBox = new Fieldset();
inputsBox.setLegend("Datos de Acceso:");
inputsBox.appendContent(iconName.getContainer());
inputsBox.appendContent(inputName.geInput());
inputsBox.appendContent(lpassword.getLabel());
inputsBox.appendContent(inputPassword.geInput());
inputsBox.appendContent(check.geInput());
inputsBox.appendContent(checkLabel.getLabel());
const buildBoxInputs = inputsBox.getElement();

const acceder = new Button();
acceder.setButton({ submit: "submit" }, { id: "acceso" });
acceder.appendContent("Acceder");
const borrar = new Button();
borrar.setButton({ reset: "reset" });
borrar.appendContent("Borrar");

const buttonsBox = new Fieldset();
buttonsBox.setLegend("Procesar acceso.");
buttonsBox.appendContent(acceder.getElement());
buttonsBox.appendContent(borrar.getElement());
const buildBoxButtons = buttonsBox.getElement();

export function accessLogin() {
    const elForm = new Form();
    elForm.setAction("");
    elForm.setMethod("get");
    elForm.appendContent(buildBoxInputs);
    elForm.appendContent(buildBoxButtons);
    document.addEventListener("DOMContentLoaded", () => {
        CreateElement.setElement(elForm.getElement(), "articleone");
    });
}

export const renderForm = document.addEventListener("DOMContentLoaded", () => {
    const verlo = new BlockContainer();
    const exit = `${accessLogin()}`;
    verlo.setContainer(exit);
    return CreateElement.setElement(verlo.getContainer());
});
```

---

#### Enlace al índice del proyecto

- [Relacíon de clases del código fuente base](./docs/index.md)
