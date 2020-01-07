---
title: Deklaracje i definicjeC++()
ms.date: 12/12/2019
ms.assetid: 678f1424-e12f-45e0-a957-8169e5fef6cb
ms.openlocfilehash: d52294b635e05f42a4c48620214a90cad609f575
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301551"
---
# <a name="declarations-and-definitions-c"></a>Deklaracje i definicjeC++()

C++ Program składa się z różnych jednostek, takich jak zmienne, funkcje, typy i przestrzenie nazw. Każda z tych jednostek musi być *zadeklarowana* , zanim będzie można jej używać. Deklaracja określa unikatową nazwę jednostki wraz z informacjami o jego typie i innych właściwościach. W C++ punkcie, w którym zadeklarowana jest nazwa, jest punktem, w którym jest on widoczny dla kompilatora. Nie można odwołać się do funkcji lub klasy, która jest zadeklarowana w późniejszym czasie w jednostce kompilacji. Zmienne powinny być deklarowane jako możliwie blisko w punkcie, w którym są używane.

W poniższym przykładzie przedstawiono niektóre deklaracje:

```cpp
#include <string>

void f(); // forward declaration

int main()
{
    const double pi = 3.14; //OK
    int i = f(2); //OK. f is forward-declared
    std::string str; // OK std::string is declared in <string> header
    C obj; // error! C not yet declared.
    j = 0; // error! No type specified.
    auto k = 0; // OK. type inferred as int by compiler.
}

int f(int i)
{
    return i + 42;
}

namespace N {
   class C{/*...*/};
}
```

W wierszu 5 jest zadeklarowana funkcja `main`. W wierszu 7 zmienna **const** o nazwie `pi` jest zadeklarowana i *zainicjowana*. W wierszu 8 liczba całkowita `i` jest zadeklarowana i inicjowana przy użyciu wartości wygenerowanej przez `f`funkcji. Nazwa `f` jest widoczna dla kompilatora z powodu *deklaracji Forward* w wierszu 3. 

W wierszu 9 jest zadeklarowana zmienna o nazwie `obj` typu `C`. Jednakże ta deklaracja zgłasza błąd, ponieważ `C` nie jest zadeklarowany do późniejszego w programie i nie jest zadeklarowana dalej. Aby naprawić ten błąd, można przenieść całą *definicję* `C` przed `main` lub w przeciwnym razie dodać do niej deklarację przesyłania dalej. To zachowanie różni się od innych języków, takich C#jak, w których funkcje i klasy mogą być używane przed ich punktem deklaracji w pliku źródłowym. 

W wierszu 10 zadeklarowana jest zmienna o nazwie `str` typu `std::string`. Nazwa `std::string` jest widoczna, ponieważ jest wprowadzana w [pliku nagłówkowym](header-files-cpp.md) `string`, który jest scalany z plikiem źródłowym w wierszu 1. `std` jest przestrzenią nazw, w której zadeklarowana jest Klasa `string`.

W wierszu 11 zostanie zgłoszony błąd, ponieważ nazwa `j` nie została zadeklarowana. Deklaracja musi dostarczyć typ, w przeciwieństwie do innych języków, takich jak javaScript. W wierszu 12 jest używane słowo kluczowe `auto`, które informuje kompilator, aby wywnioskować typ `k` na podstawie wartości, z którą jest inicjowany. Kompilator w tym przypadku wybiera `int` dla typu.  

## <a name="declaration-scope"></a>Zakres deklaracji

Nazwa wprowadzona przez deklarację jest prawidłowa w *zakresie* , w którym występuje deklaracja. W poprzednim przykładzie zmienne, które są zadeklarowane wewnątrz funkcji `main` są *zmiennymi lokalnymi*. Można zadeklarować inną zmienną o nazwie `i` poza główną, w *zakresie globalnym*i być całkowicie oddzielną jednostką. Takie Duplikowanie nazw może jednak prowadzić do pomyłki i błędów programisty i należy je unikać. W wierszu 21 Klasa `C` jest zadeklarowana w zakresie `N`przestrzeni nazw. Użycie przestrzeni nazw pozwala uniknąć *kolizji nazw*. Większość C++ standardowych nazw bibliotek jest zadeklarowanych w przestrzeni nazw `std`. Aby uzyskać więcej informacji o tym, jak reguły zakresu współdziałają z deklaracjami, zobacz [SCOPE](../cpp/scope-visual-cpp.md).

## <a name="definitions"></a>Definicje

Niektóre jednostki, w tym funkcje, klasy, wyliczenia i zmienne stałe, muszą być zdefiniowane jako uzupełnienie. *Definicja* zawiera kompilator zawierający wszystkie informacje potrzebne do generowania kodu maszynowego, gdy jednostka jest używana w dalszej części tego programu. W poprzednim przykładzie wiersz 3 zawiera deklarację dla funkcji `f` ale *Definicja* funkcji jest dostępna w wierszach od 15 do 18. W wierszu 21 Klasa `C` jest zadeklarowana i zdefiniowana (chociaż zdefiniowana Klasa nie wykonuje żadnych czynności). Zmienna stała musi być zdefiniowana, innymi słowy, w której jest przypisana wartość, w tej samej instrukcji, w której jest zadeklarowany. Deklaracja typu wbudowanego, taka jak `int` jest automatycznie definicją, ponieważ kompilator wie, ile miejsca do przydzielenia.

W poniższym przykładzie przedstawiono deklaracje, które są również definicjami:

```cpp
// Declare and define int variables i and j.
int i;
int j = 10;

// Declare enumeration suits.
enum suits { Spades = 1, Clubs, Hearts, Diamonds };

// Declare class CheckBox.
class CheckBox : public Control
{
public:
    Boolean IsChecked();
    virtual int     ChangeState() = 0;
};
```

Poniżej przedstawiono niektóre deklaracje, które nie są definicjami:

```cpp
extern int i;
char *strchr( const char *Str, const char Target );
```

## <a name="typedefs-and-using-statements"></a>Definicje typów i instrukcje using

We wcześniejszych wersjach programu C++słowo kluczowe [typedef](aliases-and-typedefs-cpp.md) jest używane do deklarowania nowej nazwy, która jest *aliasem* dla innej nazwy. Na przykład typ `std::string` jest kolejną nazwą dla `std::basic_string<char>`. Powinien być oczywisty, dlaczego programiści używają nazwy typedef, a nie nazwy rzeczywistej. W nowoczesnych C++, słowo kluczowe [using](aliases-and-typedefs-cpp.md) jest preferowane względem elementu typedef, ale pomysł jest taki sam: Nowa nazwa jest zadeklarowana dla jednostki, która jest już zadeklarowana i zdefiniowana.

## <a name="static-class-members"></a>Statyczne składowe klas

Ponieważ składowe danych klasy statycznej są zmiennymi dyskretnymi udostępnianymi przez wszystkie obiekty klasy, muszą one być zdefiniowane i zainicjowane poza definicją klasy. (Aby uzyskać więcej informacji, zobacz [klasy](../cpp/classes-and-structs-cpp.md)).

## <a name="extern-declarations"></a>deklaracje zewnętrzne

C++ Program może zawierać więcej niż jedną [jednostkę kompilacji](header-files-cpp.md). Aby zadeklarować jednostkę, która jest zdefiniowana w osobnej jednostce kompilacji, użyj słowa kluczowego [extern](extern-cpp.md) . Informacje w deklaracji są wystarczające dla kompilatora, ale jeśli nie można znaleźć definicji jednostki w kroku konsolidacji, konsolidator zgłosi błąd.

## <a name="in-this-section"></a>W tej sekcji

[Klasy magazynu](storage-classes-cpp.md)<br/>
[const](const-cpp.md)<br/>
[constexpr](constexpr-cpp.md)<br/>
[extern](extern-cpp.md)<br/>
[Inicjatory](initializers.md)<br/>
[Aliasy i definicje typów](aliases-and-typedefs-cpp.md)<br/>
[Korzystanie z deklaracji](using-declaration.md)<br/>
[volatile](volatile-cpp.md)<br/>
[decltype](decltype-cpp.md)<br/>
[Atrybuty wC++](attributes.md)<br/>

## <a name="see-also"></a>Zobacz także

[Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)<br/>
