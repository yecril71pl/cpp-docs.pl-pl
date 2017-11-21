---
title: Identyfikatory (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- decorated names
- decorated names, about decorated names
- identifiers, C++
- white space, in C++ identifiers
- identifiers [C++]
ms.assetid: 03a0dfb1-4530-4cdf-8295-5ea4dca4c1b8
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a60ce1bd87929853e57796c6ca2727fdb626e96f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="identifiers-c"></a>Identyfikatory (C++)
Identyfikator jest sekwencji znaków używany do określenia jedną z następujących czynności:  
  
-   Nazwa obiektu lub zmienna  
  
-   Klasy, struktury lub nazwą Unii  
  
-   Nazwa typu wyliczeniowego  
  
-   Element członkowski klasy, struktury, Unią lub — wyliczenie  
  
-   Funkcji lub elementu członkowskiego klasy  
  
-   Nazwa typu TypeDef  
  
-   Nazwa etykiety  
  
-   Nazwa makra  
  
-   Parametr — makro  
  
 Następujące znaki są dozwolone jako dowolny znak identyfikatora:  
  
```  
_ a b c d e f g h i j k l m  
n o p q r s t u v w x y z  
A B C D E F G H I J K L M  
N O P Q R S T U V W X Y Z  
```  
  
 Określone zakresy uniwersalne nazwy znaków również są dozwolone w identyfikatorze.  Nazwa zawierająca znaki uniwersalne w identyfikatorze nie może wyznaczyć znaku kontrolnego lub znak w zestawie znaków źródła podstawowych. Aby uzyskać więcej informacji, zobacz [zestawów znaków](../cpp/character-sets2.md). Te Unicode kod punktu numer są dozwolone zakresy jako uniwersalny nazwy znaków dowolny znak w identyfikatorze:  
  
-   00A8, 00AA, 00AD, 00AF, 00B2 00B5, 00B7 00BA, 00BC-00BE 00C 0 00 D 6, 8-00F6 00D, 00F8 00FF, 02FF 0100, 0370 167F, D 1681 180, 180F 1DBF, 1E00 1FFF, 200B - 200D, 202A 202E, 2040 203F, 2054, 206F 2060, 20CF 2070, 218F 2100, 2460-24FF, 2776-2793 00 2C-2DFF, 2E80 2FFF, 3004 3007, 3021 302F, 3031 303F, 3040 D7FF, CSA F900 FD3D, FD40 FDCF, FDF0 FE1F, FE30 FE44, FE47 FFFD 10000 1FFFD, 20000 2FFFD, 30000 3FFFD, 40000 4FFFD, 50000 5FFFD, 60000 6FFFD, 70000 7FFFD, 80000 8FFFD, 9FFFD 90000, A0000 AFFFD, D0000 BFFFD B0000, C0000-CFFFD-DFFFD, E0000 EFFFD  
  
 Następujące znaki są dozwolone jako dowolny znak w identyfikatorze oprócz pierwszego:  
  
```  
0 1 2 3 4 5 6 7 8 9  
```  
  
 Te kod punktu liczba zakresów Unicode również są dozwolone jako uniwersalny nazwy znaków dowolny znak w identyfikatorze oprócz pierwszego:  
  
-   0300-036F 1DC0 1DFF, 0 20D-20FF, FE20 FE2F  
  
 **Dotyczące firmy Microsoft**  
  
 Tylko pierwszy 2048 znaków identyfikatory Microsoft C++ są istotne. Nazwy dla typów zdefiniowanych przez użytkownika są "dekorowane" przez kompilator, aby zachować informacje o typie. Nazwa wynikowe, wraz z informacjami typu nie może być dłuższa niż 2048 znaków. (Zobacz [dekorowane nazwy](../build/reference/decorated-names.md) Aby uzyskać więcej informacji.) Czynniki wpływające długość identyfikatora ozdobione są:  
  
-   Określa, czy identyfikator oznacza obiekt typu zdefiniowanego przez użytkownika lub typ pochodny typu zdefiniowanego przez użytkownika.  
  
-   Określa, czy identyfikator Określa funkcja lub typ pochodny funkcji.  
  
-   Liczba argumentów funkcji.  
  
 Znak dolara `$` jest prawidłowym identyfikatorem znak w języku Visual C++. Visual C++ można też użyć znakom reprezentowany przez dozwolonych zakresy uniwersalne nazwy znaków w identyfikatorach. Aby korzystać z tych znaków, musisz zapisać plik przy użyciu pliku kodowanie stronę kodową, która je zawiera.  W tym przykładzie pokazano, jak rozszerzyć zarówno znaków i uniwersalne nazwy znaków mogą być używane zamiennie w kodzie.  
  
```  
// extended_identifier.cpp  
// In Visual Studio, use File, Advanced Save Options to set  
// the file encoding to Unicode codepage 1200  
struct テスト         // Japanese 'test'  
{  
    void トスト() {}  // Japanese 'toast'  
};  
  
int main() {  
    テスト \u30D1\u30F3;  // Japanese パン 'bread' in UCN form  
    パン.トスト();        // compiler recognizes UCN or literal form  
}  
```  
  
 Zakres znaków dozwolonych w identyfikatorze jest mniej restrykcyjne w przypadku kompilowania kodu C + +/ CLI kodu. Identyfikatory w kodzie skompilowanym za pomocą/CLR, należy stosować [standardowe ECMA-335: infrastruktury języka wspólnego (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
 Pierwszy znak identyfikatora muszą być litery, wielkie i małe litery, lub znaku podkreślenia ( **_** ). Ponieważ identyfikatory C++ jest uwzględniana wielkość liter, `fileName` różni się od `FileName`.  
  
 Identyfikatory nie mogą być dokładnie taką samą pisownię i przypadku jako słowa kluczowe. Identyfikatory zawierające słowa kluczowe są prawnych. Na przykład `Pint` jest identyfikatorem prawnych, mimo że zawiera on `int`, który jest słowem kluczowym.  
  
 Użyj dwóch znaków podkreślenia sekwencyjnych ( **__** ) na początku identyfikatora lub pojedynczy podkreślenia wiodące następuje polecenie wielkiej litery jest zarezerwowany dla implementacji C++ w wszystkich zakresów. Należy unikać przy użyciu jednej podkreśleniem początku następuje małej litery w nazwach z zakresem pliku z powodu konfliktów z obecne lub przyszłe identyfikatory zastrzeżone.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencje leksykalne](../cpp/lexical-conventions.md)