---
title: Biblioteka MFC DLL — często zadawane pytania
ms.date: 05/06/2019
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
ms.openlocfilehash: 9108aaf3fcface847b0391455a2aecd4d45658c4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417349"
---
# <a name="dll-frequently-asked-questions"></a>DLL — często zadawane pytania

Poniżej przedstawiono niektóre często zadawane pytania dotyczące bibliotek DLL.

- [Czy biblioteka MFC DLL może tworzyć wiele wątków?](#mfc_multithreaded_1)

- [Czy aplikacja wielowątkowa może uzyskać dostęp do biblioteki MFC DLL w różnych wątkach?](#mfc_multithreaded_2)

- [Czy istnieją jakieś klasy MFC lub funkcje, których nie można używać w bibliotece MFC DLL?](#mfc_prohibited_classes)

- [Jakich technik optymalizacji należy użyć, aby zwiększyć wydajność aplikacji klienckiej podczas ładowania?](#mfc_optimization)

- [W mojej zwykłej bibliotece DLL MFC występuje przeciek pamięci, ale mój kod wygląda dobrze. Jak mogę znaleźć przeciek pamięci?](#memory_leak)

## <a name="can-an-mfc-dll-create-multiple-threads"></a><a name="mfc_multithreaded_1"></a>Czy biblioteka MFC DLL może tworzyć wiele wątków?

Z wyjątkiem podczas inicjowania Biblioteka MFC DLL może bezpiecznie tworzyć wiele wątków, o ile używa funkcji lokalnego magazynu wątków Win32 (TLS), takich jak **Funkcja TlsAlloc** , do przydzielenia lokalnego magazynu wątków. Jeśli jednak biblioteka MFC DLL używa **__declspec (wątek)** do przydzielenia lokalnego magazynu wątków, aplikacja kliencka musi być niejawnie połączona z biblioteką DLL. Jeśli aplikacja kliencka jawnie łączy się z biblioteką DLL, wywołanie funkcji **LoadLibrary** nie załaduje pomyślnie biblioteki DLL. Aby uzyskać więcej informacji na temat zmiennych lokalnych wątków w bibliotekach DLL, zobacz [Thread](../cpp/thread.md).

Biblioteka MFC DLL, która tworzy nowy wątek MFC podczas uruchamiania, przestanie odpowiadać, gdy zostanie załadowana przez aplikację. Obejmuje to zawsze, gdy wątek jest tworzony przez `AfxBeginThread` wywołanie `CWinThread::CreateThread` lub wewnątrz:

- `InitInstance` Obiekt pochodny w zwykłej bibliotece MFC `CWinApp`dll.

- Podano `DllMain` lub **RawDllMain** funkcję w zwykłej bibliotece MFC DLL.

- Dostarczona `DllMain` lub **RawDllMain** funkcja w bibliotece DLL rozszerzenia MFC.

## <a name="can-a-multithreaded-application-access-an-mfc-dll-in-different-threads"></a><a name="mfc_multithreaded_2"></a>Czy aplikacja wielowątkowa może uzyskać dostęp do biblioteki MFC DLL w różnych wątkach?

Aplikacje wielowątkowe mogą uzyskiwać dostęp do zwykłych bibliotek DLL MFC, które łączą się dynamicznie z bibliotekami DLL MFC i MFC z różnych wątków. Aplikacja może uzyskiwać dostęp do zwykłych bibliotek DLL MFC, które statycznie łączą się z MFC z wielu wątków utworzonych w aplikacji.

## <a name="are-there-any-mfc-classes-or-functions-that-cannot-be-used-in-an-mfc-dll"></a><a name="mfc_prohibited_classes"></a>Czy istnieją jakieś klasy MFC lub funkcje, których nie można używać w bibliotece MFC DLL?

Biblioteki DLL rozszerzeń używają `CWinApp`klasy pochodnej aplikacji klienckiej. Nie mogą mieć własnej `CWinApp`klasy pochodnej.

Regularne biblioteki DLL MFC muszą mieć `CWinApp`klasę pochodną i pojedynczy obiekt tej klasy aplikacji, tak jak aplikacja MFC. W `CWinApp` przeciwieństwie `CWinApp` do obiektu aplikacji, obiekt biblioteki DLL nie ma głównej pompy komunikatów.

Należy pamiętać, że `CWinApp::Run` ponieważ mechanizm nie ma zastosowania do biblioteki DLL, aplikacja jest właścicielem głównej pompy komunikatów. Jeśli biblioteka DLL otwiera Niemodalne okna dialogowe lub ma własne główne obramowanie, główna pompa komunikatów aplikacji musi wywołać procedurę wyeksportowaną przez bibliotekę DLL, która z kolei wywołuje funkcję `CWinApp::PreTranslateMessage` członkowską obiektu aplikacji biblioteki DLL.

## <a name="what-optimization-techniques-should-i-use-to-improve-the-client-application39s-performance-when-loading"></a><a name="mfc_optimization"></a>Jakich technik optymalizacji należy użyć, aby zwiększyć wydajność aplikacji klienta&#39;s podczas ładowania?

Jeśli biblioteka DLL jest zwykłą biblioteką DLL MFC, która jest statycznie połączona z MFC, zmiana jej na zwykłą bibliotekę MFC DLL, która jest dynamicznie połączona z MFC, zmniejsza rozmiar pliku.

Jeśli biblioteka DLL ma dużą liczbę wyeksportowanych funkcji, użyj pliku. def, aby wyeksportować funkcje (zamiast używać **__declspec (dllexport)**) i użyć [atrybutu def NoName](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) pliku dla każdej wyeksportowanej funkcji. Atrybut NONAME powoduje, że tylko wartość porządkowa, a nie nazwa funkcji, która ma być przechowywana w tabeli eksportu biblioteki DLL, co zmniejsza rozmiar pliku.

Biblioteki DLL, które są niejawnie połączone z aplikacją, są ładowane podczas ładowania aplikacji. Aby zwiększyć wydajność podczas ładowania, spróbuj podzielić bibliotekę DLL na różne biblioteki DLL. Należy umieścić wszystkie funkcje, które aplikacja wywołująca musi natychmiast po załadowaniu do jednej biblioteki DLL i mieć niejawnie link do tej biblioteki DLL. Należy umieścić inne funkcje, których aplikacja wywołująca nie musi bezpośrednio korzystać z innej biblioteki DLL i ma jawnie link do tej biblioteki DLL. Aby uzyskać więcej informacji, zobacz [łączenie pliku wykonywalnego z biblioteką DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use).

## <a name="there39s-a-memory-leak-in-my-regular-mfc-dll-but-my-code-looks-fine-how-can-i-find-the-memory-leak"></a><a name="memory_leak"></a>Wystąpił&#39;s przeciek pamięci w mojej zwykłej bibliotece DLL MFC, ale mój kod wygląda dobrze. Jak mogę znaleźć przeciek pamięci?

Jedną z możliwych przyczyn przecieku pamięci jest to, że MFC tworzy obiekty tymczasowe, które są używane wewnątrz funkcji obsługi komunikatów. W aplikacjach MFC te obiekty tymczasowe są automatycznie czyszczone w `CWinApp::OnIdle()` funkcji, która jest wywoływana między przetwarzaniem komunikatów. Jednak w bibliotekach dołączanych dynamicznie MFC (dll) `OnIdle()` funkcja nie jest wywoływana automatycznie. W związku z tym obiekty tymczasowe nie są automatycznie czyszczone. Aby oczyścić obiekty tymczasowe, biblioteka DLL musi jawnie wywołać `OnIdle(1)` okresowo.

## <a name="see-also"></a>Zobacz też

[Tworzenie bibliotek DLL C/C++ w programie Visual Studio](dlls-in-visual-cpp.md)
