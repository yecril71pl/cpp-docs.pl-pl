---
title: Deklaracje i definicje (C++)
ms.date: 12/12/2019
ms.assetid: 678f1424-e12f-45e0-a957-8169e5fef6cb
ms.openlocfilehash: 688c1960e37fe74edecabebc4cb8090af9d0dd58
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228963"
---
# <a name="declarations-and-definitions-c"></a>Deklaracje i definicje (C++)

Program C++ składa się z różnych jednostek, takich jak zmienne, funkcje, typy i przestrzenie nazw. Każda z tych jednostek musi być *zadeklarowana* , zanim będzie można jej używać. Deklaracja określa unikatową nazwę jednostki wraz z informacjami o jego typie i innych właściwościach. W języku C++ punkt, w którym zadeklarowano nazwę jest punktem, w którym jest widoczny dla kompilatora. Nie można odwołać się do funkcji lub klasy, która jest zadeklarowana w późniejszym czasie w jednostce kompilacji. Zmienne powinny być deklarowane jako możliwie blisko w punkcie, w którym są używane.

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

W wierszu 5 `main` Funkcja jest zadeklarowana. W wierszu 7 **`const`** zmienna o nazwie `pi` jest zadeklarowana i *zainicjowana*. W wierszu 8 liczba całkowita `i` jest zadeklarowana i inicjowana przy użyciu wartości wygenerowanej przez funkcję `f` . Nazwa `f` jest widoczna dla kompilatora z powodu *deklaracji Forward* w wierszu 3.

W wierszu 9 `obj` jest zadeklarowana zmienna o nazwie typu `C` . Jednakże ta deklaracja zgłasza błąd, ponieważ `C` nie jest zadeklarowana do późniejszego w programie i nie jest zadeklarowana dalej. Aby naprawić ten błąd, można przenieść całą *definicję* wcześniej lub w dalszej części `C` deklaracji do `main` przodu. To zachowanie różni się od innych języków, takich jak C#, w których funkcje i klasy mogą być używane przed ich punktem deklaracji w pliku źródłowym.

W wierszu 10 `str` zadeklarowana jest zmienna o nazwie typu `std::string` . Nazwa `std::string` jest widoczna, ponieważ została wprowadzona w `string` [pliku nagłówkowym](header-files-cpp.md) , który jest scalany z plikiem źródłowym w wierszu 1. `std`jest przestrzenią nazw, w której `string` zadeklarowana jest Klasa.

W wierszu 11 zostanie zgłoszony błąd, ponieważ nazwa nie została `j` zadeklarowana. Deklaracja musi dostarczyć typ, w przeciwieństwie do innych języków, takich jak javaScript. W wierszu 12 **`auto`** słowo kluczowe jest używane, co informuje kompilator do wywnioskowania typu w `k` oparciu o wartość, z którą jest inicjowany. Kompilator w tym przypadku wybiera **`int`** Typ.  

## <a name="declaration-scope"></a>Zakres deklaracji

Nazwa wprowadzona przez deklarację jest prawidłowa w *zakresie* , w którym występuje deklaracja. W poprzednim przykładzie zmienne, które są zadeklarowane wewnątrz funkcji, `main` są *zmiennymi lokalnymi*. Można zadeklarować inną zmienną o nazwie `i` poza główną, w *zakresie globalnym*i być całkowicie oddzielną jednostką. Takie Duplikowanie nazw może jednak prowadzić do pomyłki i błędów programisty i należy je unikać. W wierszu 21 Klasa `C` jest zadeklarowana w zakresie przestrzeni nazw `N` . Użycie przestrzeni nazw pozwala uniknąć *kolizji nazw*. Większość nazw standardowej biblioteki języka C++ jest zadeklarowana w `std` przestrzeni nazw. Aby uzyskać więcej informacji o tym, jak reguły zakresu współdziałają z deklaracjami, zobacz [SCOPE](../cpp/scope-visual-cpp.md).

## <a name="definitions"></a>Definicje

Niektóre jednostki, w tym funkcje, klasy, wyliczenia i zmienne stałe, muszą być zdefiniowane jako uzupełnienie. *Definicja* zawiera kompilator zawierający wszystkie informacje potrzebne do generowania kodu maszynowego, gdy jednostka jest używana w dalszej części tego programu. W poprzednim przykładzie wiersz 3 zawiera deklarację funkcji, `f` ale *Definicja* funkcji jest dostępna w wierszach od 15 do 18. W wierszu 21 Klasa `C` jest zadeklarowana i zdefiniowana (chociaż zdefiniowana Klasa nie wykonuje żadnych czynności). Zmienna stała musi być zdefiniowana, innymi słowy, w której jest przypisana wartość, w tej samej instrukcji, w której jest zadeklarowany. Deklaracja typu wbudowanego, taka jak **`int`** jest automatycznie definicją, ponieważ kompilator wie, ile miejsca do przydzielenia.

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

W starszych wersjach języka C++ [`typedef`](aliases-and-typedefs-cpp.md) słowo kluczowe jest używane do deklarowania nowej nazwy, która jest *aliasem* dla innej nazwy. Na przykład typ `std::string` to inna nazwa dla `std::basic_string<char>` . Powinien być oczywisty, dlaczego programiści używają nazwy typedef, a nie nazwy rzeczywistej. W nowoczesnych C++ [`using`](aliases-and-typedefs-cpp.md) słowo kluczowe jest preferowane **`typedef`** , ale pomysł jest taki sam: Nowa nazwa jest zadeklarowana dla jednostki, która jest już zadeklarowana i zdefiniowana.

## <a name="static-class-members"></a>Statyczne składowe klas

Ponieważ składowe danych klasy statycznej są zmiennymi dyskretnymi udostępnianymi przez wszystkie obiekty klasy, muszą one być zdefiniowane i zainicjowane poza definicją klasy. (Aby uzyskać więcej informacji, zobacz [klasy](../cpp/classes-and-structs-cpp.md)).

## <a name="extern-declarations"></a>deklaracje zewnętrzne

Program w języku C++ może zawierać więcej niż jedną [jednostkę kompilacji](header-files-cpp.md). Aby zadeklarować jednostkę, która jest zdefiniowana w osobnej jednostce kompilacji, użyj [`extern`](extern-cpp.md) słowa kluczowego. Informacje w deklaracji są wystarczające dla kompilatora, ale jeśli nie można znaleźć definicji jednostki w kroku konsolidacji, konsolidator zgłosi błąd.

## <a name="in-this-section"></a>W tej sekcji

[Klasy magazynu](storage-classes-cpp.md)<br/>
[`const`](const-cpp.md)<br/>
[`constexpr`](constexpr-cpp.md)<br/>
[`extern`](extern-cpp.md)<br/>
[Inicjatory](initializers.md)<br/>
[Aliasy i definicje typów](aliases-and-typedefs-cpp.md)<br/>
[`using`oświadczeń](using-declaration.md)<br/>
[`volatile`](volatile-cpp.md)<br/>
[`decltype`](decltype-cpp.md)<br/>
[Atrybuty w języku C++](attributes.md)<br/>

## <a name="see-also"></a>Zobacz także

[Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)<br/>
