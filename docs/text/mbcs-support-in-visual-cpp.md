---
title: "Obsługa MBCS w programie Visual C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _mbcs
dev_langs: C++
helpviewer_keywords:
- tools [C++], MBCS support
- Asian languages [C++]
- Code Editor [C++], MBCS support
- IME [C++]
- Chinese characters [C++]
- Input Method Editor [C++], MBCS
- resource editors [C++], MBCS support
- debugger [C++], MBCS support
- character sets [C++], multibyte
- Japanese characters [C++]
- multibyte characters [C++]
- Kanji character support [C++]
- NMAKE program, MBCS support
- double-byte character sets [C++]
- IME [C++], MBCS
- Input Method Editor [C++]
- MBCS [C++], enabling
ms.assetid: 6179f6b7-bc61-4a48-9267-fb7951223e38
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bdc00509d8660d8111ff1b966b7a881a153cb6c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mbcs-support-in-visual-c"></a>Obsługa MBCS w programie Visual C++
Uruchamianych na włączone MBCS wersja systemu operacyjnego Windows 2000 lub Windows XP, system programowania Visual C++ (w tym Edytor kodu źródłowego zintegrowanego, debugera i narzędzi wiersza polecenia) jest MBCS włączone, z wyjątkiem okno pamięci.  
  
 Okno pamięci nie ma możliwości interpretowania bajtów danych jako znaki MBCS, mimo że może go zinterpretować je jako znaków ANSI lub Unicode. Znaków ANSI są zawsze 1 bajt rozmiaru i znaki Unicode są 2 bajty rozmiaru. MBCS znaki mogą być 1 lub 2 wyrażona w bajtach rozmiar i ich interpretacji zależy od stronę kodową, która jest używana. W związku z tym jest trudniejsze dla okna pamięci, aby wyświetlić niezawodnie MBCS znaków. Okno pamięci nie wiesz, które bajtów jest rozpoczęciem znaku. Deweloper wyświetlać wartości bajtów w oknie pamięci i wartość tabele, aby określić reprezentacji znaków. Jest to możliwe, ponieważ dewelopera zna adres początkowy ciąg w zależności od kodu źródłowego.  
  
 Visual C++ akceptuje znaków dwubajtowych tam, gdzie jest to zrobić. W tym nazwy ścieżki i nazwy pliku w oknach dialogowych i we wpisach tekstu w edytorze programu Visual C++ zasobów (na przykład statyczny tekst w edytorze okien dialogowych) oraz wpisy statyczny tekst w edytorze ikon. Ponadto preprocesora rozpoznaje dyrektywy niektórych znaków dwubajtowych — na przykład nazwy w plików `#include` instrukcji i mogą być argumentami **code_seg** i **data_seg** pragm. W edytorze kodu źródłowego znaków dwubajtowych w komentarzy i literały ciągu są akceptowane, lecz nie w elementy języka C/C++ (np. nazwy zmiennych).  
  
##  <a name="_core_support_for_the_input_method_editor_.28.ime.29"></a>Obsługa dla edytora Input Method Editor (IME)  
 Aplikacje napisane specjalnie dla wschodnioazjatyckich rynkach, które normalnie z niego korzystać MBCS (na przykład, Japonia) obsługuje edytora IME systemu Windows do wprowadzania zarówno znaków pojedynczego i znaków dwubajtowych. Środowisko projektowe Visual C++ zawiera pełną obsługę edytora IME. Aby uzyskać więcej informacji, zobacz [próbki edytora IME: Pokazuje, jak tryb edytora IME formantu i wdrożenie edytora IME poziom 3](http://msdn.microsoft.com/en-us/87ebdf65-cef0-451d-a6fc-d5fb64178b14).  
  
 Japoński klawiatury nie obsługują bezpośrednio znaków Kanji. Edytora IME konwertuje ciąg fonetyczny zawartych w jednym z innych alfabetach japoński (Romaji Katakana i Hiragana) możliwe oświadczeń Kanji. W przypadku niejednoznaczności, możesz wybrać kilka rozwiązań alternatywnych. Po wybraniu zamierzone znaków Kanji edytora IME przekazuje dwa `WM_CHAR` wiadomości do kontroli aplikacji.  
  
 Edytora IME aktywowany przez ALT +\` kombinację klawiszy, zostanie wyświetlony jako zestaw przycisków (wskaźnika) i okno konwersji. Aplikacja określa położenie okna punkt wstawiania tekstu. Aplikacja musi obsługiwać `WM_MOVE` i `WM_SIZE` wiadomości według położenia okna konwersji z nowej lokalizacji i rozmiaru okna docelowego.  
  
 Jeśli chcesz, aby użytkownicy mają możliwość wprowadzania znaków Kanji aplikacji, aplikacja musi obsługiwać wiadomości IME systemu Windows. Aby uzyskać więcej informacji na temat programowania w języku edytora IME, zobacz [edytora Input Method Editor](https://msdn.microsoft.com/en-us/library/ms776145.aspx).  
  
## <a name="visual-c-debugger"></a>Visual C++ — debuger  
 Debuger programu Visual C++ pozwala, aby ustawić punkty przerwania w komunikatach edytora IME. Ponadto okno pamięci można wyświetlić znaków dwubajtowych.  
  
## <a name="command-line-tools"></a>Narzędzia wiersza polecenia  
 Narzędzia wiersza polecenia języka Visual C++, w tym kompilatora, NMAKE i kompilatora zasobów (RC. EXE) są włączone MBCS. /C — opcja kompilatora zasobów umożliwia zmienić domyślną stronę kodową podczas kompilowania zasobów aplikacji.  
  
 Aby zmienić domyślne ustawienia regionalne w czasie kompilacji kodu źródłowego, należy użyć [#pragma setlocale](../preprocessor/setlocale.md).  
  
## <a name="graphical-tools"></a>Narzędzia graficzne  
 Narzędzia Visual C++ systemu, takie jak Spy ++ i zasobów, narzędzia, do edycji w pełni obsługuje ciągów edytora IME.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa zestawów znaków wielobajtowych (zestawy MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)   
 [Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)