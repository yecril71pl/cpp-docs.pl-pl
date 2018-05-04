---
title: scanf — specyfikacje szerokości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr100.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- scanf
dev_langs:
- C++
helpviewer_keywords:
- scanf function, width specification
ms.assetid: 94b4e8fe-c4a2-4799-8b6c-a2cf28ffb09c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0052f4b270366b2f3aa1e1550f790efcb860597
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="scanf-width-specification"></a>scanf — Specyfikacje szerokości
Te informacje dotyczą interpretacji ciągów formatu w `scanf` rodziny funkcji, takich jak także bezpiecznego wersji `scanf_s`. Funkcje te zwykle założenie, że strumień wejściowy jest podzielony na sekwencja tokenów. Tokeny są rozdzielone odstępem (miejsce, karty lub nowego wiersza) lub w przypadku typów wartości liczbowych, do końca fizycznych typu danych numerycznych wskazywany przez pierwszego znaku, której nie można przekonwertować na tekst wartości liczbowych. Specyfikacja szerokości można jednak powoduje analizowanie danych wejściowych zatrzymać przed zakończeniem fizycznych tokenu.  
  
 *Szerokość* specyfikacji składa się ze znaków między `%` i specyfikatora typu pola, które mogą obejmować dodatnią liczbą całkowitą o nazwie *szerokość* pola i co najmniej jeden znak rozmiar pola, które również mogą być uważane za Modyfikatory typ pola, takie jak wskazuje, czy jest typu Liczba całkowita wskazująca **krótki** lub **długi**. Znaki te są określane jako prefiks rozmiaru.  
  
## <a name="the-width-field"></a>Szerokość pola  
 *Szerokość* pole jest dodatnią dziesiętną liczbą całkowitą kontrolowanie maksymalną liczbę znaków do odczytu dla tego pola. Nie więcej niż *szerokość* znaki są przekonwertować i przechowywać w odpowiedniej `argument`. Mniej niż *szerokość* znaki mogą być odczytu, jeśli występuje znak odstępu (miejsce, karty lub nowego wiersza) lub znak, której nie można przekonwertować zgodnie z danego formatu przed *szerokość* zostanie osiągnięty.  
  
 Specyfikacja szerokości jest odrębną z argumentem rozmiaru buforu wymagane przez bezpieczny wersje tych funkcji (tj. `scanf_s`, `wscanf_s`itp.). W poniższym przykładzie Specyfikacja szerokości wynosi 20, co oznacza, że do 20 znaków mają być odczytane ze strumienia wejściowego. Długość buforu jest 21, w tym miejsca do 20 znaków plus terminatorem null:  
  
```  
char str[21];  
scanf_s("%20s", str, 21);  
```  
  
 Jeśli *szerokość* pole nie jest używane, `scanf_s` spróbuje odczytać całego token w ciągu. Jeśli określony rozmiar nie jest wystarczająco duży, aby pomieścić cały token, nic nie zostanie zapisany na ciąg docelowego. Jeśli *szerokość* pole jest określony, następnie pierwszy *szerokość* znaków w tokenie zostanie zapisany w ciągu docelowego wraz z terminatorem null.  
  
## <a name="the-size-prefix"></a>Prefiks rozmiaru  
 Opcjonalne prefiksy **h**, **l**, **ll**, **komputerach 64**, i **L** rozmiaru `argument`(długich i krótkich, znaków jednobajtowych lub znaków dwubajtowych w zależności od znaku typu, które modyfikują). Te znaki specyfikacji formatu są używane z typów znaków w `scanf` lub `wscanf` funkcji, aby określić interpretacji argumentów, jak pokazano w poniższej tabeli. Prefiks typu **komputerach 64** to rozszerzenie firmy Microsoft i nie jest ANSI zgodny. Wpisz znaki i ich znaczenie są opisane w tabeli "Typ znaków dla funkcji scanf" [scanf — znaki pola typu](../c-runtime-library/scanf-type-field-characters.md).  
  
> [!NOTE]
>  **h**, **l**, i **L** prefiksy są rozszerzenia Microsoft, gdy jest używany z danymi typu `char`.  
  
### <a name="size-prefixes-for-scanf-and-wscanf-format-type-specifiers"></a>Rozmiar prefiksy scanf i wscanf — typ formatu specyfikatory  
  
|Aby określić|Użyj prefiksu|Ze specyfikatorem typu|  
|----------------|----------------|-------------------------|  
|**double**|**l**|**e**, **E**, **f**, **g**, lub **G**|  
|**Long double** (taki sam, jak podwójna)|**L**|**e**, **E**, **f**, **g**, lub **G**|  
|**długie int**|**l**|**d**, **i**, **o**, **x**, lub **X**|  
|**Long unsigned int**|**l**|**u**|  
|**długie long**|**wszystko**|**d**, **i**, **o**, **x**, lub **X**|  
|`short int`|**h**|**d**, **i**, **o**, **x**, lub **X**|  
|**krótkich liczb całkowitych bez znaku**|**h**|**u**|  
|__**int64**|**I64**|**d**, **i**, **o**, **u**, **x**, lub **X**|  
|Znaków z `scanf`|**h**|**c** lub **C**|  
|Znaków z `wscanf`|**h**|**c** lub **C**|  
|Szerokich znaków z `scanf`|**l**|**c** lub **C**|  
|Szerokich znaków z `wscanf`|**l**|**c**, lub **C**|  
|Jednobajtowe — ciąg znaków z `scanf`|**h**|**s** lub **S**|  
|Jednobajtowe — ciąg znaków z `wscanf`|**h**|**s** lub **S**|  
|Ciąg znaków dwubajtowych z `scanf`|**l**|**s** lub **S**|  
|Ciąg znaków dwubajtowych z `wscanf`|**l**|**s** lub **S**|  
  
 W poniższych przykładach użyto **h** i **l** z `scanf_s` funkcje i `wscanf_s` funkcje:  
  
```  
scanf_s("%ls", &x, 2);     // Read a wide-character string  
wscanf_s(L"%hC", &x, 2);    // Read a single-byte character  
```  
  
 Jeśli funkcja niezabezpieczone w `scanf` rodziny, Pomiń parametr rozmiaru wskazujący długość buforu poprzedniego argumentu.  
  
## <a name="reading-undelimited-strings"></a>Odczytywanie Undelimited ciągów  
 Do odczytu nie rozdzielone odstępem ciągów znaków, zestaw znaków w nawiasach (**[**) mogą być zastępowane dla **s** znaku typu (ciąg). Zestaw znaków w nawiasach jest określana jako ciąg formantu. Odpowiednie pole wejściowe jest do odczytu do pierwszego znaku, który nie występuje w ciągu formantu. Jeśli pierwszy znak w zestawie jest daszek (**^**), efekt jest wycofywany: pole wejściowe jest do odczytu do pierwszego znaku, który pojawia się w pozostałej części zestawu znaków.  
  
 Należy pamiętać, że **% [a-z]** i **% [z-a]** będą interpretowane jako odpowiednik **%[abcde...z]**. Jest to wspólny `scanf` rozszerzenia funkcji, ale należy pamiętać, że standardu ANSI nie wymaga.  
  
## <a name="reading-unterminated-strings"></a>Niezakończony odczytu ciągów  
 Aby ciąg bez przechowywania znak końcowy null ('\0'), należy użyć specyfikację `%` *n *** c** gdy *n* jest dziesiętną liczbą całkowitą. W takim przypadku **c** znaku typu wskazuje, że argument jest wskaźnik do tablicy znaków. Następne *n* znaki są odczytywane ze strumienia wejściowego w określonej lokalizacji, a nie znak null ('\0') jest dołączony. Jeśli *n* nie zostanie określony, jego wartość domyślna to 1.  
  
## <a name="when-scanf-stops-reading-a-field"></a>Gdy scanf zatrzymuje odczytywania pola  
 `scanf` Funkcja skanuje każdego pola wejściowego, znak po znaku. Może zatrzymać, odczytywania określonego pola wejściowego, przed jego znak spacji z różnych powodów:  
  
-   Określona szerokość został osiągnięty.  
  
-   Nie można przekonwertować następny znak jak określono.  
  
-   Następny znak powoduje konflikt z znaku w ciągu kontroli, która powinna być zgodna.  
  
-   Następny znak nie może występować w zestawie znaku.  
  
 Niezależnie od przyczyny gdy `scanf` funkcja zatrzymuje odczytywania pola wejściowego, dalej pole wejściowe uważa się rozpoczynać się od pierwszego znaku nieprzeczytana. Znak powodujące konflikt, jeśli istnieje, jest traktowany jako nieprzeczytana i jest pierwszym znakiem dalej pole wejściowe lub pierwszy znak w kolejnych operacji odczytu dla strumienia wejściowego.  
  
## <a name="see-also"></a>Zobacz też  
 [scanf, _scanf_l —, wscanf — _wscanf_l —](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [scanf_s —, _scanf_s_l —, wscanf_s — _wscanf_s_l —](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [Pola specyfikacji formatu: funkcji wscanf](../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)   
 [scanf, znaki pola typu](../c-runtime-library/scanf-type-field-characters.md)