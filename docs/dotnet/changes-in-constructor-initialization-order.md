---
title: Zmiany w kolejności inicjowania konstruktorów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constructors, C++
ms.assetid: 8892c38d-6bf7-4cf7-ac8f-15e052135a79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fd54e9810131f3ddfabe458c70ddef081568a9cd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397692"
---
# <a name="changes-in-constructor-initialization-order"></a>Zmiany w kolejności inicjowania konstruktorów

Kolejności inicjowania konstruktorów klasy zmienił się z zarządzanych rozszerzeń dla C++ do Visual C++.

## <a name="comparison-of-constructor-initialization-order"></a>Porównywanie kolejności inicjowania konstruktorów

W obszarze zarządzanych rozszerzeń języka C++ Konstruktor inicjowania wystąpił w następującej kolejności:

1. Konstruktor klasy bazowej, jeśli istnieje, jest wywoływana.

1. Listy inicjowania klasy jest oceniany.

1. Kod konstruktora klasy zostaje wykonana.

Ta kolejność wykonywania jest zgodna z konwencjami ten sam, jak natywny programowania języka C++. Nowy język Visual C++, określa kolejność wykonywania następujących klas CLR:

1. Listy inicjowania klasy jest oceniany.

1. Konstruktor klasy bazowej, jeśli istnieje, jest wywoływana.

1. Kod konstruktora klasy zostaje wykonana.

Należy pamiętać, że ta zmiana dotyczy tylko klas CLR; macierzystych klas w programie Visual C++ nadal zgodne z konwencjami poprzedniego. W obu przypadkach te reguły narastać Kaskadowo w górę w całym łańcuchu całej hierarchii danej klasy.

Rozważmy następujący przykład kodu przy użyciu zarządzanych rozszerzeń języka C++:

```
__gc class A
{
public:
   A() : _n(1)
   {
   }

protected:
   int _n;
};

__gc class B : public A
{
public:
   B() : _m(_n)
   {
   }
private:
   int _m;
};
```

Następujące kolejności inicjowania konstruktorów opisane powyżej, powinniśmy zobaczyć następującej kolejności wykonywania, jeśli nowe wystąpienia klasy `B` są wykonane:

1. Konstruktor klasy bazowej `A` zostanie wywołana. `_n` Elementu członkowskiego jest inicjowany do `1`.

1. Listy inicjowania klasy `B` jest oceniany. `_m` Elementu członkowskiego jest inicjowany do `1`.

1. Treść kodu klasy `B` jest wykonywany.

Teraz należy wziąć pod uwagę ten sam kod w nowej składni języka Visual C++:

```
ref class A
{
public:
   A() : _n(1)
   {
   }

protected:
   int _n;
};

ref class B : A
{
public:
   B() : _m(_n)
   {
   }
private:
   int _m;
};
```

Kolejność wykonywania, jeśli nowe wystąpienia klasy `B` są tworzone w nowym składnia jest następująca:

1. Listy inicjowania klasy `B` jest oceniany. `_m` Elementu członkowskiego jest inicjowany do `0` (`0` jest wartością niezainicjowanej `_m` składowej klasy).

1. Konstruktor klasy bazowej `A` zostanie wywołana. `_n` Elementu członkowskiego jest inicjowany do `1`.

1. Treść kodu klasy `B` jest wykonywany.

Należy pamiętać, że podobnej składni daje różne wyniki dla tych przykładów kodu. Konstruktor klasy `B` zależy od wartości z klasy bazowej `A` zainicjować członków. Jednakże Konstruktor dla klasy `A` nie została jeszcze wywołana. Takie zależności mogą być szczególnie niebezpieczne, gdy odziedziczoną klasę zależy od alokację pamięci lub zasobów występuje w konstruktorze klasy bazowej.

## <a name="what-this-means-going-from-managed-extensions-for-c-to-visual-c-2010"></a>Jakie oznacza to, przechodząc z zarządzanych rozszerzeń dla języka C++ do Visual C++ 2010

W wielu przypadkach zmiany kolejności wykonywania konstruktorów klas powinny być przezroczyste do programisty należy, ponieważ klasy bazowe nie pojęcie zachowanie klasy dziedziczone. Jednak jak te przykłady kodu ilustrują, Konstruktory klasy dziedziczone mogą znacznie wpływać podczas ich listy inicjowania są zależne od wartości składowych klasy bazowej. Podczas przenoszenia kodu z zarządzanych rozszerzeń dla C++ do nowej składni, należy wziąć pod uwagę przeniesienie takich konstrukcji treść konstruktora klasy gdzie wykonywania musi występować jako ostatnia.

## <a name="see-also"></a>Zobacz też

[Typy zarządzane (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[Konstruktory](../cpp/constructors-cpp.md)
