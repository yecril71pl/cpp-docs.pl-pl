---
title: Jednostki tłumaczeniowe i powiązania (C++)
ms.date: 12/11/2019
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
ms.openlocfilehash: 791ec53d4df863b218db463f2b9b9401bf6f466d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374317"
---
# <a name="translation-units-and-linkage"></a>Jednostki translacji i połączenie

W programie C++ *symbol*, na przykład zmienna lub nazwa funkcji, może być zadeklarowany dowolną liczbę razy w jego zakresie, ale można go zdefiniować tylko raz. Ta reguła jest "One Definition Rule" (ODR). *Deklaracja* wprowadza (lub ponownie wprowadza) nazwę do programu. *Definicja* wprowadza nazwę. Jeśli nazwa reprezentuje zmienną, definicja jawnie inicjuje ją. *Definicja funkcji* składa się z podpisu plus treść funkcji. Definicja klasy składa się z nazwy klasy, po której następuje blok, który zawiera listę wszystkich członków klasy. (Obiekty funkcji członkowskich mogą być opcjonalnie zdefiniowane oddzielnie w innym pliku).

W poniższym przykładzie przedstawiono niektóre deklaracje:

```cpp
int i;
int f(int x);
class C;
```

W poniższym przykładzie przedstawiono kilka definicji:

```cpp
int i{42};
int f(int x){ return x * i; }
class C {
public:
   void DoSomething();
};
```

Program składa się z co najmniej jednej *jednostki tłumaczeniowej*. Jednostka tłumaczenia składa się z pliku implementacji i wszystkich nagłówków, które zawiera bezpośrednio lub pośrednio. Pliki implementacyjne zazwyczaj mają rozszerzenie pliku *cpp* lub *cxx*. Pliki nagłówkowe zazwyczaj mają rozszerzenie *h* lub *hpp*. Każda jednostka tłumaczenia jest kompilowana niezależnie przez kompilator. Po zakończeniu kompilacji konsolidator scala skompilowane jednostki tłumaczeniowe w jeden *program.* Naruszenia reguły ODR zazwyczaj są wyświetlane jako błędy konsolidatora. Błędy konsolidatora występują, gdy ta sama nazwa ma dwie różne definicje w różnych jednostkach tłumaczenia.

Ogólnie rzecz biorąc, najlepszym sposobem, aby zmienna była widoczna w wielu plikach, jest umieszczenie jej w pliku nagłówka. Następnie dodaj dyrektywę #include w każdym pliku *cpp,* który wymaga deklaracji. Dodając *osłony dołączania* wokół zawartości nagłówka, upewnij się, że nazwy, które deklaruje, są zdefiniowane tylko raz.

W języku C++20 [moduły](modules-cpp.md) są wprowadzane jako ulepszona alternatywa dla plików nagłówkowych.

W niektórych przypadkach może być konieczne zadeklarowanie zmiennej globalnej lub klasy w pliku *cpp.* W takich przypadkach należy sposób, aby poinformować kompilatora i konsolidatora, jaki rodzaj *powiązania* nazwa ma. Typ powiązania określa, czy nazwa obiektu ma zastosowanie tylko do jednego pliku, czy do wszystkich plików. Pojęcie powiązania dotyczy tylko nazw globalnych. Pojęcie powiązania nie ma zastosowania do nazw, które są zadeklarowane w zakresie. Zakres jest określony przez zestaw otaczających nawiasów klamrowych, takich jak w funkcji lub definicji klasy.

## <a name="external-vs-internal-linkage"></a>Połączenie zewnętrzne a wewnętrzne

*Funkcja wolna* jest funkcją zdefiniowaną w zakresie globalnym lub obszaru nazw. Zmienne globalne inne niż const i wolne funkcje domyślnie mają *powiązania zewnętrzne;* są one widoczne z dowolnej jednostki tłumaczeniowej w programie. W związku z tym żaden inny obiekt globalny nie może mieć tej nazwy. Symbol z *wewnętrznym powiązaniem* lub *bez powiązania* jest widoczny tylko w jednostce tłumaczenia, w której jest zadeklarowany. Jeśli nazwa ma wewnętrzne powiązanie, ta sama nazwa może istnieć w innej jednostce tłumaczenia. Zmienne zadeklarowane z definicjami klas lub organami funkcyjnymi nie mają powiązania.

Można wymusić połączenie wewnętrzne nazwy globalnej, wyraźnie deklarując ją jako **statyczną**. Ogranicza to jego widoczność do tej samej jednostki tłumaczenia, w której jest zadeklarowana. W tym kontekście **statyczne** oznacza coś innego niż po zastosowaniu do zmiennych lokalnych.

Następujące obiekty mają domyślnie wewnętrzne powiązanie:

- const obiektów
- constexpr obiekty
- definicje typów
- obiekty statyczne w zakresie obszaru nazw

Aby nadać obiektowi const zewnętrzne powiązanie, zadeklaruj go jako **extern** i przypisz mu wartość:

```cpp
extern const int value = 42;
```

Zobacz [extern](extern-cpp.md) aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

[Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)
