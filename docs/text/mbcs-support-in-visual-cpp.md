---
title: Obsługa MBCS w programie Visual C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f595a048d9f2e5795f69b7d1da6c4c6cf4ca0fa2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42608683"
---
# <a name="mbcs-support-in-visual-c"></a>Obsługa MBCS w programie Visual C++
Po uruchomieniu na Windows w wersji dla systemów z obsługą MBCS, systemie programistycznym Visual C++ (w tym kodu źródłowego zintegrowane narzędzia edytora, debugera i wiersza polecenia) jest MBCS włączone, z wyjątkiem okna pamięci.  
  
 Okno pamięci nie interpretuje bajtów danych znaków MBCS, mimo że można interpretował je jako znaki ANSI lub Unicode. Znaki ANSI, są zawsze 1 bajt, rozmiar i znaki Unicode są rozmiar 2 bajtów. Za pomocą MBCS znaki mogą być 1 lub 2 bajtów i ich interpretację zależy od tego, stronę kodową, która jest używana. W związku z tym trudno jest niezawodne wyświetlenia znaków MBCS w oknie pamięci. Okno pamięci nie wiedzieć, które bajt jest początku znak. Deweloper można wyświetlić wartości bajtów w oknie pamięci i sprawdzać wartości w tabelach w celu określenia reprezentacji znaków. Jest to możliwe, ponieważ wie, deweloper adres początkowy ciągu na podstawie kodu źródłowego.  
  
 Visual C++ akceptuje znaków dwubajtowych, wszędzie tam, gdzie jest to zrobić. W tym nazwy ścieżek i nazwy plików w oknach dialogowych i wpisów tekstowych w Edytor zasobów Visual C++ (na przykład statyczny tekst w edytorze okien dialogowych) i wpisy statyczny tekst w edytorze ikon. Ponadto, preprocesor rozpoznaje niektórych dyrektyw znaków dwubajtowych — na przykład plik nazwy w `#include` instrukcji i jako argumenty do `code_seg` i `data_seg` pragmy. W edytorze kodu źródłowego znaków dwubajtowych w komentarzach i literały ciągów są akceptowane, ale nie w elementy języka C/C++ (np. nazwy zmiennych).  
  
##  <a name="_core_support_for_the_input_method_editor_.28.ime.29"></a> Obsługa dla edytora metody wprowadzania (IME)  
 Aplikacje napisane z myślą o wschodnioazjatyckich rynków, na których zazwyczaj używają MBCS (na przykład, Japonia) obsługuje Windows IME do wprowadzania zarówno pojedynczego i znaków dwubajtowych znaków. Środowisko projektowe Visual C++ zawiera pełne wsparcie dla edytora IME. Aby uzyskać więcej informacji, zobacz [edytora IME próbki: Pokazuje, jak tryb IME kontroli i implementowanie edytora IME poziom 3](http://msdn.microsoft.com/87ebdf65-cef0-451d-a6fc-d5fb64178b14).  
  
 Klawiatury japońskiej nie obsługują bezpośrednio znaków Kanji. Edytora IME konwertuje ciąg fonetycznych wprowadzane w jednej z innych alfabety japoński (Romaji, Katakana lub znaków Hiragana) do jego możliwe reprezentacje Kanji. W przypadku niejednoznaczności, możesz wybrać kilka rozwiązań alternatywnych. Po wybraniu zamierzony znaków Kanji edytora IME przekazuje dwa `WM_CHAR` wiadomości do kontrolowania aplikacji.  
  
 Edytora IME aktywowany przez ALT +\` kombinacji klawiszy, jest wyświetlana jako zestaw przycisków (wskaźnik) i okno konwersji. Aplikacja umieszcza okno w punkcie wstawiania tekstu. Aplikacja musi obsłużyć `WM_MOVE` i `WM_SIZE` wiadomości według położenia okna konwersji do nowej lokalizacji i rozmiaru okna docelowego.  
  
 Jeśli chcesz, aby użytkownicy twojej aplikacji, aby mieć możliwość wprowadzania znaków Kanji, aplikacja musi obsługiwać komunikaty Windows edytora IME. Aby uzyskać więcej informacji na temat programowania w edytorze IME zobacz [edytora Input Method Editor](/previous-versions/windows/desktop/ms776145\(v=vs.85\)).  
  
## <a name="visual-c-debugger"></a>Debuger programu Visual C++  
 Debuger Visual C++ umożliwia ustawianie punktów przerwania w edytorze IME komunikaty w protokole. Ponadto znaki dwubajtowe można wyświetlić w oknie pamięci.  
  
## <a name="command-line-tools"></a>Narzędzia wiersza polecenia  
 Narzędzia wiersza polecenia języka Visual C++, w tym kompilator, NMAKE i kompilator zasobów (RC. Z rozszerzeniem EXE), mają włączoną MBCS. /C — opcja kompilatora zasobów można użyć, aby zmienić domyślną stronę kodową, podczas kompilowania zasobów aplikacji.  
  
 Aby zmienić domyślne ustawienia regionalne w czasie kompilacji kodu źródłowego, należy użyć [#pragma setlocale](../preprocessor/setlocale.md).  
  
## <a name="graphical-tools"></a>Narzędzia graficzne  
 Narzędzia oparte na Visual C++ Windows, takich jak narzędzie Spy ++ i zasobów, narzędzia, do edycji w pełni obsługiwać ciągi znaków edytora IME.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa zestawów znaków wielobajtowych (zestawy MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)   
 [Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)