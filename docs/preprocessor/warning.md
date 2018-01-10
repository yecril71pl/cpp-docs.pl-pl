---
title: "Ostrzeżenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- warning_CPP
- vc-pragma.warning
dev_langs: C++
helpviewer_keywords:
- pragmas, warning
- push pragma warning
- pop warning pragma
- warning pragma
ms.assetid: 8e9a0dec-e223-4657-b21d-5417ebe29cc8
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 275ca0a1101141ef1c0f4217597a644a6dbd8c46
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="warning-pragma"></a>Ostrzeżenie Pragma
Umożliwia selektywne modyfikacji zachowania wiadomości ostrzeżeń kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```
#pragma warning(   
    warning-specifier : warning-number-list [; warning-specifier : warning-number-list...] )  
#pragma warning( push[ ,n ] )  
#pragma warning( pop )  
```  
  
## <a name="remarks"></a>Uwagi  
Dostępne są następujące parametry specyfikator ostrzeżenie.  
  
|Ostrzeżenie — Specyfikator|Znaczenie|  
|------------------------|-------------|  
|`1, 2, 3, 4`|Zastosuj danego poziomy do określonego ostrzeżeniami. Włącza to również określonego ostrzeżenie, że jest domyślnie wyłączone.|  
|`default`|Ostrzeżenie zachowanie zresetowana do wartości domyślnej. Włącza to również określonego ostrzeżenie, że jest domyślnie wyłączone. To ostrzeżenie będzie generowane w lokalizacji domyślnej, udokumentowane, poziom.<br /><br /> Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../preprocessor/compiler-warnings-that-are-off-by-default.md).|  
|`disable`|Nie wydaje określony komunikaty ostrzegawcze.|  
|`error`|Raport określonych ostrzeżeń jako błędy.|  
|`once`|Wyświetl komunikaty określony tylko jeden raz.|  
|`suppress`|Wypchnięcia bieżący stan pragma na stosie, wyłącza określony ostrzeżenia dla następnego wiersza i tak, aby stan pragma jest resetowany będzie wyświetlana na stosie ostrzeżenie.|  
  
 Przedstawia następującą instrukcję kodu, który `warning-number-list` parametr może zawierać wiele numerów ostrzeżeń, a wiele `warning-specifier` parametry można określić w tym samym dyrektywa pragma.  
  
```cpp  
#pragma warning( disable : 4507 34; once : 4385; error : 164 )  
```  
  
 To jest funkcjonalnym odpowiednikiem następującego kodu.  
  
```cpp  
// Disable warning messages 4507 and 4034.  
#pragma warning( disable : 4507 34 )  
  
// Issue warning 4385 only once.  
#pragma warning( once : 4385 )  
  
// Report warning 4164 as an error.  
#pragma warning( error : 164 )  
```  
  
 Kompilator dodaje 4000 dowolną liczbę ostrzeżenie należącą do zakresu od 0 do 999.  
  
 Ostrzeżenie liczb w zakresie 4700-4999, które są skojarzone z generowania kodu, stan ostrzeżenia obowiązywać, gdy kompilator napotka otwarty nawias klamrowy funkcji będzie obowiązywać w pozostałej części funkcji. Przy użyciu `warning` pragma w funkcji zmiany stanu ostrzeżenia, która jest większa niż 4699 liczba zostaną wprowadzone dopiero po zakończeniu funkcji. W poniższym przykładzie przedstawiono poprawne położenie `warning` pragm, aby wyłączyć komunikat ostrzegawczy generowania kodu, a następnie przywróć ją.  
  
```cpp  
// pragma_warning.cpp  
// compile with: /W1  
#pragma warning(disable:4700)  
void Test() {  
   int x;  
   int y = x;   // no C4700 here  
   #pragma warning(default:4700)   // C4700 enabled after Test ends  
}  
  
int main() {  
   int x;  
   int y = x;   // C4700  
}  
```  
  
 Należy zauważyć, że w całej funkcji body ostatniego ustawienie `warning` pragma będzie obowiązywać dla całej funkcji.  
  
## <a name="push-and-pop"></a>Wypychania i Pop  
 `warning` Pragma obsługuje również następującej składni, gdzie `n` reprezentuje poziom ostrzeżeń (od 1 do 4).  
  
 `#pragma warning( push [ , n ] )`  
  
 `#pragma warning( pop )`  
   
 Pragma `warning( push )` zapisuje bieżący stan ostrzeżenia dla każdego ostrzeżenia. Pragma `warning( push, n )` zapisuje bieżący stan każdego ostrzeżenia i Ustawia globalną ostrzeżenie `n`.  
  
 Pragma `warning( pop )` POP ostatni stan ostrzeżenia wypychana na stosie. Wszelkie zmiany wprowadzone w stan ostrzegawczy między `push` i `pop` zostaną cofnięte. Rozważmy następujący przykład:  
  
```cpp  
#pragma warning( push )  
#pragma warning( disable : 4705 )  
#pragma warning( disable : 4706 )  
#pragma warning( disable : 4707 )  
// Some code  
#pragma warning( pop )   
```  
  
 Na koniec tego kodu `pop` przywraca stan każdego ostrzeżenia (w tym 4705, 4706 i 4707) jakie były na początku kodu.  
  
 Podczas pisania pliki nagłówkowe, można użyć `push` i `pop` aby zagwarantować, że stan ostrzegawczy zmiany wprowadzone przez użytkownika uniemożliwia nagłówki kompilowanie poprawnie. Użyj `push` na początku nagłówka i `pop` na końcu. Na przykład jeśli masz nagłówek, który nie kompiluje się prawidłowo na poziomie ostrzeżenia 4 następujący kod będzie zmienić poziom ostrzeżeń do 3 i przywrócić oryginalny poziom ostrzeżeń na końcu nagłówka.  
  
```cpp  
#pragma warning( push, 3 )  
// Declarations/definitions  
#pragma warning( pop )   
```  
  
 Aby uzyskać więcej informacji o kompilatora pominąć opcje, które ułatwiają ostrzeżenia, zobacz [/FI](../build/reference/fi-name-forced-include-file.md) i [/w](../build/reference/compiler-option-warning-level.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)