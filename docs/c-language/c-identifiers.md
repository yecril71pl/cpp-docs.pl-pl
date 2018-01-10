---
title: "Identyfikatory języka C | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- identifiers, C
- naming identifiers
- identifiers
- symbols, C identifiers
- identifiers, case sensitivity
- symbols, case sensitivity
ms.assetid: d02edbbc-85a0-4118-997b-84ee6b972eb6
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dfe8ab231d6bf4051cc730ff1beb23f93a8f301d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c-identifiers"></a>Identyfikatory języka C
"Identyfikatory" lub "symbole" są podane nazwy zmiennych, typów, funkcji i etykiet w programie. Nazwy identyfikatorów muszą różnić się w pisowni i liter od dowolnego słowa kluczowe. Słowa kluczowe (C lub Microsoft) nie można używać jako identyfikatorów; są one zarezerwowane do użytku specjalnych. Utworzysz identyfikatora, określając w deklaracji zmiennej, typu lub funkcji. W tym przykładzie `result` jest identyfikatorem zmienna typu Liczba całkowita i `main` i `printf` to identyfikator nazwy funkcji.  
  
```  
#include <stdio.h>  
  
int main()  
{  
    int result;  
  
    if ( result != 0 )  
        printf_s( "Bad file handle\n" );  
}  
```  
  
 Po zadeklarowaniu, służy identyfikator w późniejszym instrukcjach program do odwoływania się do skojarzona wartość.  
  
 Specjalny rodzaj identyfikatora, etykiet instrukcji, mogą być używane w `goto` instrukcje. (Deklaracje są opisane w [deklaracje i typy](../c-language/declarations-and-types.md) etykiety instrukcji opisanych w [goto i Labeled — instrukcje](../c-language/goto-and-labeled-statements-c.md).)  
  
## <a name="syntax"></a>Składnia  
 *Identyfikator*:  
 *cyfrą*  
  
 *Identyfikator cyfrą*  
  
 *Identyfikator cyfrowy*  
  
 `nondigit`: jeden z  
 **_ b c d e f g h i j k l m n ie p q r s t u v w x y z**  
  
 **B C D E F G H I J K L M N IE P Q R S T U V W X Y Z**  
  
 `digit`: jeden z  
 **0 1 2 3 4 5 6 7 8 9**  
  
 Pierwszy znak nazwy identyfikatora musi być `nondigit` (to znaczy pierwszy znak musi być znaku podkreślenia ani wielkie i małe litery). ANSI umożliwia sześciu znaczących znaki w nazwie identyfikatora zewnętrznego i 31 w nazwach identyfikatorów wewnętrznych (w funkcji). Zewnętrzne identyfikatory (tych zadeklarowana w zakresie globalnym lub zadeklarowana przy użyciu klasy magazynu `extern`) mogą paść dodatkowe ograniczenia nazewnictwa, ponieważ takie identyfikatory muszą być przetwarzane przez inne oprogramowanie, takie jak linkery.  
  
 **Dotyczące firmy Microsoft**  
  
 Mimo że ANSI umożliwia 6 znaki znaczące zewnętrznych identyfikatorów, nazw i 31 w nazwach identyfikatorów wewnętrznych (w funkcji), kompilator Microsoft C umożliwia 247 znaków w nazwie identyfikatora wewnętrznych lub zewnętrznych. Jeśli nie są związane z zgodność ANSI, można zmodyfikować to ustawienie domyślne na mniejszą lub większą liczbę przy użyciu /H (Ograniczaj długość nazw zewnętrznych) opcja.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
 Kompilator języka C uwzględnia wielkie i małe litery jako różne znaki. Ta funkcja o nazwie "wielkość liter" umożliwia tworzenie unikatowych identyfikatorów, które mają taki sam Pisownia ale o innej przypadków co najmniej jednej litery. Na przykład każdego z następujących identyfikatorów jest unikatowa:  
  
```  
add  
ADD  
Add  
aDD  
```  
  
 **Dotyczące firmy Microsoft**  
  
 Nie zaznaczaj nazwy identyfikatorów zaczynających dwóch znaków podkreślenia lub podkreśleniem następuje polecenie wielkiej litery. Standard ANSI C umożliwia nazwy identyfikatorów, które zaczynają się od kombinacji tych znaków mają zostać zarezerwowane do użytku kompilatora. Identyfikatory o zakresie poziomu plików powinny również nie miały nazwę nadaną przez podkreślenia i małą literę jako dwa pierwsze litery. Nazwy identyfikatorów, które zaczynają się od tych znaków również są zastrzeżone. Konwencja firma Microsoft używa podkreślenia i wielką literę zacząć nazwy makr i podwójnego podkreślenia nazw — słowo kluczowe specyficzne dla firmy Microsoft. Aby uniknąć konfliktów nazw, należy zawsze wybierać identyfikator nazw, które nie rozpoczynają się co najmniej dwa znaki podkreślenia lub nazwy zaczynające się od znaku podkreślenia następuje polecenie wielkiej litery.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
 Poniżej przedstawiono przykłady prawidłowych identyfikatorów zgodnych ze standardami ANSI lub Microsoft ograniczenia nazewnictwa:  
  
```  
j  
count  
temp1  
top_of_page  
skip12  
LastNum  
```  
  
 **Dotyczące firmy Microsoft**  
  
 Identyfikatory w plikach źródłowych jest uwzględniana wielkość liter, domyślnie, symboli w plikach obiektu nie są. Microsoft C traktuje identyfikatorów w ramach jednostki kompilacji jako wielkość liter.  
  
 Konsolidator firmy Microsoft jest rozróżniana wielkość liter. Należy określić wszystkie identyfikatory spójnie zgodnie z liter.  
  
 "Zestaw znaków źródła" to zestaw dozwolonych znaków, które mogą być wyświetlane w plikach źródłowych. Dla Microsoft C zestaw źródłowy jest standardowy zestaw znaków ASCII. Zestaw znaków źródła i zestaw znaków wykonania obejmują używany jako sekwencje specjalne znaków ASCII. Zobacz [stałe znakowe](../c-language/c-character-constants.md) informacji na temat znaków wykonania można ustawić.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
 Identyfikator ma 'scope', czyli region programu, w którym jest znany i "powiązanie", która określa, czy tej samej nazwie w innym zakresie odwołuje się do tego samego identyfikatora. W tych tematach opisano szczegółowo w [okres istnienia, zakres, widoczność i połączenie](../c-language/lifetime-scope-visibility-and-linkage.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy języka C](../c-language/elements-of-c.md)