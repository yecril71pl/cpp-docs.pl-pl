---
title: Deklaracje tablicy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- multidimensional arrays
- declaring arrays
- arrays [C++], declaring
ms.assetid: 5f958b97-cef0-4058-bbc6-37c460aaed9b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 74cfdf5393487ddd2cda7d478c0940c6db74b35a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="array-declarations"></a>Deklaracje tablicy
"Array deklaracji" nazwy tablicy i określa typ swoich elementów. Można również zdefiniować liczbę elementów w tablicy. Zmienna typu tablicy jest traktowany jako wskaźnika na typ elementów tablicy.  
  
## <a name="syntax"></a>Składnia  
 `declaration`:  
 *Specyfikatory deklaracji w init listy deklarator* opt**;**  
  
 *init — deklarator — lista*:  
 *init — deklarator*  
  
 *init — deklarator — lista* **,***init deklarator*   
  
 *init — deklarator*:  
 *deklarator*  
  
 *deklarator***=***inicjatora*   
  
 `declarator`:  
 *wskaźnik* opt*bezpośrednio deklarator*  
  
 *deklarator bezpośrednio*:  
 *deklarator bezpośrednio***[***wyrażenia* opt**]**   
  
 Ponieważ *wyrażenia* jest opcjonalny, składnia ma dwie formy:  
  
-   Pierwszy formularz definiuje zmienną tablicową. *Wyrażenia* argument w nawiasach określa liczbę elementów w tablicy. *Wyrażenia*, jeśli jest obecny, musi mieć typ całkowity, a wartość większą niż zero. Każdy element ma typ przez *specyfikatora typu*, które mogą być dowolnego typu, z wyjątkiem `void`. Element tablicy nie może być typem funkcji.  
  
-   Drugi formularz deklaruje zmienną, która została zdefiniowana w innym miejscu. To ciąg *wyrażenia* argument w nawiasach kwadratowych, ale nie nawiasy kwadratowe. Można użyć tego formularza, tylko jeśli wcześniej zainicjowana tablicy on zadeklarowany jako parametr, lub zadeklarowana go jako odwołanie do tablicy jawnie zdefiniowany w innych miejscach w programie.  
  
 W obu formach *deklarator bezpośrednio* nazwy zmiennej i będzie można zmodyfikować typu zmiennej. Nawiasy kwadratowe (**[**) następujące *deklarator bezpośrednio* zmodyfikować deklarator na typ tablicy.  
  
 Kwalifikatory typu może występować w deklaracji obiektu typu tablicy, ale kwalifikatory stosowane do elementów, a nie samego tablicy.  
  
 Wykonując deklarator tablicy z listą stałej wyrażenia w nawiasach kwadratowych w tym formularzu można zadeklarować tablicy tablic (tablicy "wielowymiarowej"):  
  
```  
  
type-specifier  
declarator [constant-expression] [constant-expression] ...  
```  
  
 Każdy *wyrażenia* w nawiasach definiuje liczbę elementów w określonym wymiarze: dwuwymiarowa tablice zawierają dwóch wyrażeń w nawiasach kwadratowych, trójwymiarowy tablice mają trzy i tak dalej. Pierwsze wyrażenie stałej można pominąć, jeśli masz zainicjować tablicy on zadeklarowany jako parametr, lub zadeklarowana go jako odwołanie do tablicy jawnie zdefiniowany w innych miejscach w programie.  
  
 Można zdefiniować tablic wskaźników do różnych typów obiektów przy użyciu deklaratorów złożonych, zgodnie z opisem w [interpretowanie więcej Deklaratorów złożonych](../c-language/interpreting-more-complex-declarators.md).  
  
 Tablice są przechowywane przez wiersz. Na przykład następujące tablicy obejmuje dwa wiersze z trzech kolumn:  
  
```  
char A[2][3];  
```  
  
 Trzy kolumny pierwszego wiersza są przechowywane najpierw następuje trzy kolumny w drugim wierszu. Oznacza to, najbardziej szybko zależy ostatniego indeks dolny.  
  
 Aby odwołać się do pojedynczego elementu tablicy, użyj wyrażenia indeksu dolnego zgodnie z opisem w [operatory przyrostka](../c-language/postfix-operators.md).  
  
## <a name="examples"></a>Przykłady  
 Poniższe przykłady przedstawiają deklaracje tablicy:  
  
```  
float matrix[10][15];  
```  
  
 Tablicą dwuwymiarową o nazwie `matrix` ma 150 elementów, każdy o **float** typu.  
  
```  
struct {  
    float x, y;  
} complex[100];  
```  
  
 Jest to deklarację tablicy struktury. Ta tablica ma 100 elementów; Każdy element jest strukturą zawierającego dwa elementy członkowskie.  
  
```  
extern char *name[];  
```  
  
 Ta instrukcja deklaruje typ i nazwa tablicy wskaźników do `char`. Rzeczywiste definicji `name` występuje w innym miejscu.  
  
 **Dotyczące firmy Microsoft**  
  
 Rozmiar jest typu Liczba całkowita wymagane do przechowywania maksymalny rozmiar tablicy **size_t**. Zdefiniowany w pliku nagłówka STDDEF. H, **size_t** jest `unsigned int` z zakresem 0x00000000 do 0x7CFFFFFF.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)