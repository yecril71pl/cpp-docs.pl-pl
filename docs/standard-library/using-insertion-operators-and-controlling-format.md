---
title: "Korzystanie z operatorów wstawiania i formatu kontrolującego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: insertion operators
ms.assetid: cdefe986-6548-4cd1-8a67-b431d7d36a1c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2860a0bfd050c4e2a86e948c7008327d237bc5ab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-insertion-operators-and-controlling-format"></a>Korzystanie z operatorów wstawiania i formatu kontrolującego
W tym temacie przedstawia sposób kontrolowania format oraz sposobu tworzenia operatorów wstawiania własnych klas. Wstawiania (**<<**) operatora, który jest wcześniej zaplanowane dla wszystkie standardowe typy danych języka C++, wysyła bajtów do obiektu strumienia wyjściowego. Operatory wstawienia współpracować z wstępnie zdefiniowanych "manipulatory,", które są elementami, które zmienić domyślny format liczby całkowitej argumentów.  
  
 Można kontrolować format z następujących opcji:  
  
- [Szerokość danych wyjściowych](#vclrfoutputwidthanchor3)  
  
- [Wyrównanie](#vclrfalignmentanchor4)  
  
- [Dokładność](#vclrfprecisionanchor5)  
  
- [Podstawa](#vclrfradixanchor6)  
  
##  <a name="vclrfoutputwidthanchor3"></a>Szerokość danych wyjściowych  
 Aby wyrównać dane wyjściowe, określ szerokość danych wyjściowych dla każdego elementu przez umieszczenie `setw` manipulatora w strumieniu, przez wywołanie **szerokość** funkcję elementu członkowskiego. W tym przykładzie prawej wyrównuje wartości w kolumnie co najmniej 10 znaków:  
  
```  
// output_width.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main( )  
{  
   double values[] = { 1.23, 35.36, 653.7, 4358.24 };  
   for( int i = 0; i < 4; i++ )  
   {  
      cout.width(10);  
      cout << values[i] << '\n';  
   }  
}  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```  
    1.23 
    35.36 
    653.7 
4358.24  
```  
  
 Spacje wiodące są dodawane do żadnej wartości mniej niż 10 znaków.  
  
 Aby uzupełnić pola, użyj **wypełnienia** funkcji członkowskiej, która ustawia wartości znak dopełnienia dla pól zawierających określona szerokość. Ustawieniem domyślnym jest pusty. Aby konsoli kolumny liczb z gwiazdką, zmodyfikuj poprzedniej **dla** pętli w następujący sposób:  
  
```  
for(int i = 0; i <4; i++)  
{  
    cout.width(10);

 cout.fill('*');

    cout <<values[i] <<endl;  
}  
```  
  
 `endl` Manipulatora zastępuje znaku nowego wiersza (`'\n'`). Dane wyjściowe wyglądają następująco:  
  
```  
******1.23  
*****35.36  
*****653.7  
***4358.24  
```  
  
 Aby określić szerokości dla elementów danych w tej samej linii, użyj `setw` manipulatora:  
  
```  
// setw.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iomanip>  
using namespace std;  
  
int main( )  
{  
   double values[] = { 1.23, 35.36, 653.7, 4358.24 };  
   char *names[] = { "Zoot", "Jimmy", "Al", "Stan" };  
   for( int i = 0; i < 4; i++ )  
      cout << setw( 6 )  << names[i]  
           << setw( 10 ) << values[i] << endl;  
}  
```  
  
### <a name="output"></a>Dane wyjściowe  
 **Szerokość** funkcja członkowska jest zadeklarowana w \<iostream >. Jeśli używasz `setw` lub innych manipulatora z argumentami, musi zawierać \<iomanip — >. W danych wyjściowych parametrów są podane w zakresie szerokość 6 i liczb całkowitych w polu Szerokość 10:  
  
```  
    Zoot 1.23  
Jimmy     35.36  
    Al 653.7  
    Stan 4358.24  
```  
  
 Ani `setw` ani **szerokość** obcina wartości. Jeśli dane wyjściowe w formacie przekracza szerokość Wyświetla całą wartość, mogą ulec precyzję strumienia. Zarówno `setw` i **szerokość** mają wpływ na następujące pole. Szerokość pola zostanie przywrócony do jego domyślne zachowanie (szerokość niezbędne) po wydrukowaniu jedno pole. Jednak inne opcje format strumienia obowiązują do momentu zmiany.  
  
##  <a name="vclrfalignmentanchor4"></a>Wyrównanie  
 Dane wyjściowe strumieni domyślny tekst wyrównany do prawej. Do lewej align nazwy w poprzednim przykładzie i wyrównanie do prawej liczb, Zastąp **dla** pętli w następujący sposób:  
  
```  
for (int i = 0; i <4; i++)  
    cout <<setiosflags(ios::left)  
 <<setw(6)  <<names[i]  
 <<resetiosflags(ios::left)  
 <<setw(10) <<values[i] <<endl;  
```  
  
 Dane wyjściowe wyglądają następująco:  
  
```  
Zoot        1.23  
Jimmy      35.36  
Al         653.7  
Stan     4358.24  
```  
  
 Ustawiono flagi left-align przy użyciu [setiosflags](../standard-library/iomanip-functions.md#setiosflags) manipulatora z `left` modułu wyliczającego. Ten moduł wyliczający jest zdefiniowany w [ios](../standard-library/basic-ios-class.md) klasy, więc musi zawierać odwołanie **ios::** prefiks. [Resetiosflags](../standard-library/iomanip-functions.md#resetiosflags) manipulatora wyłącza flagi left-align. W odróżnieniu od **szerokość** i `setw`, efekt `setiosflags` i `resetiosflags` jest trwały.  
  
##  <a name="vclrfprecisionanchor5"></a>Dokładność  
 Wartość domyślna dla liczb zmiennoprzecinkowych dokładność jest sześć. Na przykład numer 3466.9768 drukuje jako 3466.98. Aby zmienić sposób drukuje tę wartość, należy użyć [setprecision](../standard-library/iomanip-functions.md#setprecision) manipulatora. Manipulatora ma dwie flagi: [stałej](../standard-library/ios-functions.md#fixed) i [naukowych](../standard-library/ios-functions.md#scientific). Jeśli [stałej](../standard-library/ios-functions.md#fixed) ustawiono numer odbitek jako 3466.976800. Jeśli **naukowych** jest ustawiona, wyświetla jako 3.4669773 + 003.  
  
 Do wyświetlania liczb zmiennoprzecinkowych pokazano [wyrównanie](#vclrfalignmentanchor4) z jedną cyfrę znaczące, Zastąp **dla** pętli w następujący sposób:  
  
```  
for (int i = 0; i <4; i++)  
    cout <<setiosflags(ios::left)  
 <<setw(6)    
 <<names[i]  
 <<resetiosflags(ios::left)  
 <<setw(10)   
 <<setprecision(1)  
 <<values[i]   
 <<endl;  
```  
  
 Program drukuje tej listy:  
  
```  
Zoot          1  
Jimmy     4e+001  
Al        7e+002  
Stan      4e+003  
```  
  
 Aby wyeliminować notacji naukowej, Wstaw niniejszych przed **dla** Pętla:  
  
```  
cout <<setiosflags(ios::fixed);
```  
  
 Notacji stałej program drukuje z jednej cyfry po przecinku.  
  
```  
Zoot         1.2  
Jimmy       35.4  
Al         653.7  
Stan      4358.2  
```  
  
 Jeśli zmienisz **ios::fixed** flaga **ios::scientific**, program drukuje to:  
  
```  
Zoot    1.2e+000  
Jimmy   3.5e+001  
Al      6.5e+002  
Stan    4.4e+003  
```  
  
 Ponownie program drukuje jednej cyfry po przecinku. Jeśli dowolny **ios::fixed** lub **ios::scientific** jest ustawiona wartość dokładności określa liczbę cyfr po punkcie dziesiętnym. Jeśli żadna flaga jest ustawiona, wartość precyzji określa całkowitą liczbę cyfr znaczących. `resetiosflags` Manipulatora usuwa te flagi.  
  
##  <a name="vclrfradixanchor6"></a>Podstawa  
 **Gru**, **oct**, i **szesnastkowych** manipulatory ustawić podstawy domyślny dla danych wejściowych i wyjściowych. Na przykład po wstawieniu **szesnastkowych** manipulatora do strumienia wyjściowego obiektu poprawnie tłumaczy reprezentacji wewnętrznej danych liczb całkowitych w formacie szesnastkowym danych wyjściowych. Liczby są wyświetlany cyfr poprzez f liter [wielkich](../standard-library/ios-functions.md#uppercase) flaga jest Wyczyść (ustawienie domyślne); w przeciwnym razie są wyświetlane wielkimi literami. Podstawa domyślny jest **gru** (dziesiętne).  
  
## <a name="quoted-strings-c14"></a>Ciągi cudzysłowie (C ++ 14)  
 Podczas wstawiania ciągu w strumieniu, możesz łatwo pobierać te same parametry przez wywołanie funkcji Członkowskich stringstream::str(). Jednak jeśli chcesz użyć operatora wyodrębniania można wstawić strumienia do nowego ciągu w późniejszym czasie, może wystąpić nieoczekiwany wynik ponieważ >> operator domyślnie zostanie zatrzymane po napotkaniu pierwszy znak odstępu.  
  
```  
 
std::stringstream ss;  
std::string inserted = "This is a sentence.";  
std::string extracted;  
 
ss <<inserted;  
ss>> extracted;  
 
std::cout <<inserted;     //  This is a sentence.  
std::cout <<extracted;   //   This  
```  
  
 Można ręcznie rozwiązać ten problem, ale aby dwustronną komunikację ciąg wygodniejsze, C ++ 14 dodaje `std::quoted` strumienia manipulatora w `<iomanip>`. Podczas wstawiania `quoted()` otaczający ciąg ogranicznikiem (podwójny cudzysłów "" "domyślnie) i podczas wyodrębniania manipuluje strumienia można wyodrębnić wszystkie znaki, dopóki nie napotkano końcowy ogranicznik. Wszystkie osadzone cudzysłowy są anulowane się od znaku ucieczki ("\\\\" domyślnie).  
  
 Ograniczniki znajdują się tylko w obiekcie strumienia; nie istnieją w ciągu wyodrębnić, ale są obecne w ciągu zwróconego przez [basic_stringstream::str](../standard-library/basic-stringstream-class.md#str)().  
  
 Zachowanie spacji operacji wstawiania i wyodrębniania jest niezależna od jak ciąg są reprezentowane w kodzie, więc ujętego w cudzysłów operator przydaje się niezależnie od tego, czy ciąg wejściowy jest nieprzetworzonego literału ciągu lub ciągu regularne. Ciąg wejściowy, niezależnie od jego format można osadzania oferty, podziały wiersza, kart i tak dalej i wszystkie one będą zachowane manipulatora quoted().  
  
 Aby uzyskać dodatkowe informacje i przykłady pełny kod, zobacz [cytowaną] — brokenlink — (.. / Topic/%3Cios%3E%20functions.md#quoted).  
  
## <a name="see-also"></a>Zobacz też  
 [Strumienie wyjściowe](../standard-library/output-streams.md)   

