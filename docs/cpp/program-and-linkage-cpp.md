---
title: Program i połączenie (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4154f0951b46b1c8badc0224845d2881cc8ad573
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="program-and-linkage--c"></a>Program i połączenie (C++)

W programu C++ każdy globalne symbol można zdefiniować tylko raz, nawet jeśli program zawiera wiele jednostek tłumaczenia. Jednostka tłumaczenia składa się z plikiem implementacji (.cpp, .hpp, .cxx itp.) oraz wszystkie nagłówki, które zawiera bezpośrednio lub pośrednio. Program składa się z co najmniej jednej jednostki tłumaczenia ze sobą powiązane. 

## <a name="linkage-vs-scope"></a>Połączenie, a zakres

Pojęcie *połączenie* odwołuje się do widoczność globalne symbole (np. zmienne nazwy typu i nazwy funkcji) w programie jako całość przez jednostki tłumaczenia. Pojęcie *zakres* odwołuje się do symboli, które są zadeklarowane w bloku, takich jak przestrzeni nazw, klasy lub treści funkcji. Takie symbole są widoczne tylko w zakresie, w którym są zdefiniowane; pojęcie powiązanie nie ma zastosowania do nich.

## <a name="external-vs-internal-linkage"></a>Zewnętrzny, a połączenie wewnętrzne

Zmienne globalne non-const i wolnego funkcje domyślnie mają połączenie zewnętrzne; są one widoczne z dowolnej jednostki tłumaczenia w programie. To zachowanie można przesłonić, jawnie je jako deklarowanie **statycznych** co ogranicza ich widoczność do tej samej jednostce tłumaczenia, w którym jest zadeklarowany. Ta znaczenie **statycznych** różni się od jego znaczenia w przypadku zastosowania do zmiennych lokalnych. Zmienne zadeklarowane jako **const** mieć powiązania wewnętrznego domyślnie.

## <a name="extern-constexpr-linkage"></a>Zewnętrzne połączenie constexpr

We wcześniejszych wersjach programu Visual Studio kompilator zawsze udzielił constexpr zmiennej połączenie wewnętrzne nawet wtedy, gdy zmienna została oznaczona jako zewnętrzny. W Visual Studio 2017 wersji 15,5 cala, nowy przełącznik (/ Zc:externConstexpr) umożliwia poprawne zachowanie zgodnych standardów. Po pewnym czasie będzie to wartość domyślna.

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

Jeśli plik nagłówka zawiera constexpr zmiennych extern zadeklarowane, musi być oznaczony **__declspec(selectany)** Aby poprawnie zawierać jego deklaracji zduplikowanych połączone:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="see-also"></a>Zobacz też

 [Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)