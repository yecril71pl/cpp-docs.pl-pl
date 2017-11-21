---
title: Pola bitowe C | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- bitfields
- bit fields
ms.assetid: 9faf74c4-7fd5-4b44-ad18-04485193d06e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0ebc62a975e534d89fd99dbb05a65e8d6cb379bc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="c-bit-fields"></a>Pola bitowe języka C
Oprócz deklaratorów dla elementów członkowskich struktury lub Unii deklaratorze struktury można też określoną liczbę bitów, nazywany "pole bitowe". Jego długość jest ustawiona z deklarator nazw pól dwukropkiem. Pola bitowego jest interpretowany jako typ całkowity.  
  
## <a name="syntax"></a>Składnia  
 *Struktura deklarator*:  
 *deklarator*  
  
 *Specyfikator typu deklarator* opt**:** *wyrażenie stałej*  
  
 *Wyrażenia* Określa szerokość pola w bitach. *Specyfikatora typu* dla `declarator` musi być `unsigned int`, **podpisany int**, lub `int`i *wyrażenia* musi być nieujemna wartość całkowita. Jeśli wartość wynosi zero, nie ma deklaracji `declarator`. Tablice pól bitowych, wskaźników do pól bitowych i funkcji zwracających pola bitowe nie są dozwolone. Opcjonalny `declarator` nazwy pola bitowego. Pola bitowe mogą być deklarowane tylko w ramach struktury. Address-of — operator (**&**) nie można zastosować do pola bitowego składników.  
  
 Pola bitowe bez nazwy nie może być przywoływany i ich zawartość w czasie wykonywania jest nieoczekiwane. One może służyć jako pola "zastępczego", do celów wyrównania. Pole bitowe bez nazwy, w których szerokość jest określony jako 0 gwarantuje magazynu dla elementu członkowskiego w następujących *struktury deklaracji listy* zaczyna się od `int` granic.  
  
 Pola bitowe musi również być wystarczająco długie, by zawierać wzorca bitowego. Na przykład te dwie instrukcje są niedozwolone:  
  
```  
short a:17;        /* Illegal! */  
int long y:33;     /* Illegal! */  
```  
  
 W tym przykładzie definiuje jest tablicą dwuwymiarową struktur o nazwie `screen`.  
  
```  
struct   
{  
    unsigned short icon : 8;  
    unsigned short color : 4;  
    unsigned short underline : 1;  
    unsigned short blink : 1;  
} screen[25][80];  
```  
  
 Tablica zawiera elementy 2000. Każdy element jest struktura poszczególnych zawierający cztery elementy pola bitowego: `icon`, `color`, `underline`, i `blink`. Rozmiar każdej struktury jest dwa bajty.  
  
 Pola bitowe mieć tej samej semantyki jako typu Liczba całkowita. Oznacza to, że pola bitowego jest używane w wyrażeniach w dokładnie tak samo, jak zmienna typu tego samego podstawowego będzie służyć bez względu na liczbę bitów w pole bitowe.  
  
 **Dotyczące firmy Microsoft**  
  
 Bit pola zdefiniowane jako `int` są traktowane jako podpisany. Umożliwia rozszerzenie Microsoft ze standardem ANSI C `char` i **długi** typów (zarówno **podpisany** i `unsigned`) dla pól bitowych. Bez nazwy pól bitowych z typu podstawowego **długi**, **krótki**, lub `char` (**podpisany** lub `unsigned`) wymusić wyrównanie do granicy odpowiednie do typu podstawowego.  
  
 Pola bitowe są przydzielane w liczbą całkowitą z przedziału od najmniej znaczący najbardziej znaczącego bitu. W poniższym kodzie  
  
```  
struct mybitfields  
{  
    unsigned short a : 4;  
    unsigned short b : 5;  
    unsigned short c : 7;  
} test;  
  
int main( void );  
{  
    test.a = 2;  
    test.b = 31;  
    test.c = 0;  
}  
```  
  
 bity może być ułożone w następujący sposób:  
  
```  
00000001 11110010  
cccccccb bbbbaaaa  
```  
  
 Ponieważ rodziny 8086 procesorów przechowuje bajcie wartości będące liczbami całkowitymi przed bajcie liczb całkowitych `0x01F2` powyżej powinny być przechowywane w pamięci fizycznej jako `0xF2` następuje `0x01`.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje struktur](../c-language/structure-declarations.md)