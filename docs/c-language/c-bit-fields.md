---
title: Pola bitowe języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- bitfields
- bit fields
ms.assetid: 9faf74c4-7fd5-4b44-ad18-04485193d06e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b3e828af6232dec6ebfb4558fdb8501c7f90abb
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757490"
---
# <a name="c-bit-fields"></a>Pola bitowe języka C
Oprócz deklaratorów elementów członkowskich struktury lub Unii deklaratora struktury można też określoną liczbę bitów, o nazwie "pole bitowe". Jego długość jest ustawiona za pomocą dwukropka z deklaratora dla nazwy pola. Pole bitowe są interpretowane jako typ całkowitoliczbowy.  
  
## <a name="syntax"></a>Składnia

*struct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator typu* *deklaratora*<sub>zoptymalizowany pod kątem</sub> **:** *wyrażenia stałego*
  
*Wyrażenie_stałe* Określa szerokość pola w bitach. *Specyfikator typu* dla `declarator` musi być `unsigned int`, **podpisany int**, lub `int`i *wyrażenie_stałe* musi być nieujemna wartość liczby całkowitej. Jeśli wartość wynosi zero, nie ma deklaracji `declarator`. Tablice pól bitowych, wskaźniki do pola bitowe i funkcji zwracających pola bitowe nie są dozwolone. Opcjonalny `declarator` nazwy pola bitowego. Pola bitowe mogą być deklarowane tylko w ramach struktury. Operator address-of (**&**) nie można zastosować do pola bitowego składników.  
  
Nie można odwoływać się do pola bitowe bez nazwy, a ich zawartość w czasie wykonywania są nieprzewidywalne. One może służyć jako pola "fikcyjny" do celów wyrównania. Pole bitowe bez nazwy, w której szerokość jest określone jako 0 gwarantuje, że magazyn dla elementu członkowskiego, postępując w *struktury deklaracji listy* zaczyna się od `int` granic.  
  
Pola bitowe również musi być wystarczająco długi, by zawierać wzorca bitowego. Na przykład następujące dwie instrukcje są niedozwolone:  
  
```  
short a:17;        /* Illegal! */  
int long y:33;     /* Illegal! */  
```  
  
Ten przykład definiuje dwuwymiarową tablicę struktury o nazwie `screen`.  
  
```  
struct   
{  
    unsigned short icon : 8;  
    unsigned short color : 4;  
    unsigned short underline : 1;  
    unsigned short blink : 1;  
} screen[25][80];  
```  
  
Tablica zawiera elementy 2000. Każdy element jest struktura poszczególne zawierający cztery pola bitowego elementy członkowskie: `icon`, `color`, `underline`, i `blink`. Rozmiar struktury jest dwubajtowa.  
  
Pola bitowe mieć tą samą semantyką jako typ liczby całkowitej. Oznacza to, że pole bitowe jest używany w wyrażeniach w taki sam sposób, zmienną ten sam typ podstawowy zostałyby użyte, niezależnie od tego, ile bitów znajdują się w pole bitowe.  
  
**Microsoft Specific**  
  
Zdefiniowane jako pola bitowe `int` jest traktowany jako podpisany. Rozszerzenie Microsoft do standardu ANSI C umożliwia `char` i **długie** typów (zarówno **podpisany** i `unsigned`) dla pól bitowych. Nienazwane pola bitowego z typem podstawowym **długie**, **krótki**, lub `char` (**podpisany** lub `unsigned`) wymusić wyrównanie na granicy odpowiednie do typu podstawowego.  
  
Pola bitowe są przydzielane w ramach całkowitą od najmniej znaczącego najbardziej znaczący bit. W poniższym kodzie  
  
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
  
bity mogłoby być ułożone w następujący sposób:  
  
```  
00000001 11110010  
cccccccb bbbbaaaa  
```  
  
Ponieważ procesorami z rodziny 8086 przechowuje bajcie liczb całkowitych, przed bajcie liczb całkowitych `0x01F2` powyżej powinny być przechowywane w pamięci fizycznej jako `0xF2` następuje `0x01`.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
[Deklaracje struktur](../c-language/structure-declarations.md)