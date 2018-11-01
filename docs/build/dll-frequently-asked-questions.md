---
title: Biblioteki MFC DLL — często zadawane pytania
ms.date: 11/04/2016
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
ms.openlocfilehash: 4d6490691583162fc95042601bd85566f693d049
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629141"
---
# <a name="dll-frequently-asked-questions"></a>DLL — często zadawane pytania

Poniżej są niektóre często zadawane pytania (FAQ), informacje o bibliotekach DLL.

- [Biblioteki MFC DLL, można tworzyć wiele wątków?](#mfc_multithreaded_1)

- [Aplikacji wielowątkowych, ma dostęp do biblioteki MFC DLL w różnych wątkach?](#mfc_multithreaded_2)

- [Istnieją dowolnej klasy lub funkcje MFC, które nie można używać w bibliotece MFC DLL?](#mfc_prohibited_classes)

- [Jakich technik optymalizacji należy używać, aby zwiększyć wydajność aplikacji klienckiej podczas ładowania?](#mfc_optimization)

- [Występuje przeciek pamięci w mojej zwykłej bibliotece DLL MFC, ale mój kod wygląda dobrze. Jak mogę znaleźć przeciek pamięci?](#memory_leak)

## <a name="mfc_multithreaded_1"></a> Biblioteki MFC DLL, można tworzyć wiele wątków?

Z wyjątkiem podczas inicjowania biblioteki MFC DLL można bezpiecznie tworzenia wielu wątków tak długo, jak używa wątek Win32, w magazynie lokalnym (TLS) funkcje takie jak **TlsAlloc** można przydzielić pamięci lokalnej wątku. Jednakże jeśli korzysta z biblioteki MFC DLL **__declspec(thread)** można przydzielić pamięci lokalnej wątku, aplikacja kliencka musi niejawnie połączona z biblioteki DLL. Jeśli aplikacja kliencka łączy jawnie do biblioteki DLL, wywołanie **LoadLibrary** nie zostanie pomyślnie załadować biblioteki DLL. Aby uzyskać więcej informacji na temat zmiennych thread-local w bibliotekach DLL, zobacz [wątku](../cpp/thread.md).

Biblioteki MFC DLL, która tworzy nowy wątek MFC podczas uruchamiania przestanie odpowiadać, gdy jest ładowany przez aplikację. Obejmuje to zawsze wtedy, gdy wątek jest tworzony przez wywołanie `AfxBeginThread` lub `CWinThread::CreateThread` wewnątrz:

- `InitInstance` z `CWinApp`-pochodzi obiekt w zwykłej biblioteki MFC DLL.

- Podany `DllMain` lub **RawDllMain** funkcji w zwykłej biblioteki MFC DLL.

- Podany `DllMain` lub **RawDllMain** funkcji w DLL rozszerzenia MFC.

## <a name="mfc_multithreaded_2"></a> Aplikacji wielowątkowych, ma dostęp do biblioteki MFC DLL w różnych wątkach?

Wielowątkowe aplikacje mogą uzyskiwać dostęp do zwykłych bibliotekach MFC dll, która łączy dynamicznie MFC biblioteki DLL rozszerzeń MFC z różnych wątków. A począwszy od Visual C++ w wersji 4.2, aplikacji mogą uzyskiwać dostęp do zwykłych bibliotekach MFC dll, która statycznie łączy do MFC z wielu wątków, utworzone w aplikacji.

Przed wersji 4.2 tylko jeden wątek zewnętrznych można dołączyć do zwykłej biblioteki MFC DLL, które są połączone statycznie z MFC.

Pamiętaj, że termin USRDLL nie jest już używany w dokumentacji języka Visual C++. Regularne biblioteki DLL MFC, która jest połączone statycznie z MFC ma takie same charakterystyki jak dawny USRDLL.

## <a name="mfc_prohibited_classes"></a> Istnieją dowolnej klasy lub funkcje MFC, które nie można używać w bibliotece MFC DLL?

Użyj biblioteki DLL rozszerzenia `CWinApp`-klasy aplikacji klienckiej. Mogą one mieć własne `CWinApp`-klasy pochodnej.

regularne biblioteki DLL MFC musi mieć `CWinApp`-pochodne klasy i pojedynczy obiekt tej klasy aplikacji, tak jak w aplikacji MFC. W odróżnieniu od `CWinApp` obiekt aplikacji, `CWinApp` obiekt biblioteki DLL nie ma "pompy komunikatów głównego".

Należy pamiętać, że ponieważ `CWinApp::Run` mechanizm nie ma zastosowania do biblioteki DLL, aplikacja jest właścicielem pompy komunikatów głównego. Jeśli ma główne okno ramowe własnej biblioteki DLL lub otwiera Niemodalne okna dialogowe, pompy komunikatów główny aplikacji musi wywołać procedurę eksportowanych przez DLL, która z kolei wywołuje `CWinApp::PreTranslateMessage` funkcja elementu członkowskiego obiektu aplikacji DLL.

## <a name="mfc_optimization"></a> Jakich technik optymalizacji należy użyć, aby zwiększyć aplikacja kliencka&#39;s wydajności podczas ładowania?

Jeśli biblioteka DLL jest zwykłej biblioteki MFC DLL, które jest połączone statycznie z MFC, zmieniając go na zwykły biblioteki MFC DLL łączonej dynamicznie z MFC zmniejsza rozmiar pliku.

Jeśli biblioteka DLL ma dużą liczbę eksportowanych funkcji, należy użyć pliku .def, aby wyeksportować funkcje (zamiast **__declspec(dllexport)**) i użyć pliku .def [noname — atrybut](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) na każdym wyeksportowanej funkcji. Noname — atrybut powoduje, że wartości porządkowej, a nie nazwę funkcji mają być przechowywane w tabeli eksportu biblioteki DLL, co zmniejsza rozmiar pliku.

Biblioteki dll, które są niejawnie połączona z aplikacją są ładowane podczas ładowania aplikacji. Aby poprawić wydajność podczas ładowania, spróbuj dzielenia biblioteki DLL do różnych bibliotek DLL. Umieść wszystkie funkcje, których potrzebuje aplikacja wywołująca, natychmiast po ładowania do jedną bibliotekę DLL i mieć aplikacja wywołująca niejawne łącze do tej biblioteki DLL. Umieścić inne funkcje, które aplikacja wywołująca nie wymaga się natychmiast w innej bibliotece DLL i mieć aplikacja jawnie utworzyć łącze do tej biblioteki DLL. Aby uzyskać więcej informacji, zobacz [określić, której metody łączenia użyjesz](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use).

## <a name="memory_leak"></a> Brak&#39;s przeciek pamięci w mojej zwykłej bibliotece DLL MFC, ale mój kod wygląda dobrze. Jak mogę znaleźć przeciek pamięci?

Jedną z możliwych przyczyn przeciek pamięci jest, że MFC tworzy obiekty tymczasowe, które są używane w funkcji obsługi komunikatów. W aplikacjach MFC takie obiekty tymczasowe są automatycznie czyszczone w `CWinApp::OnIdle()` funkcja, która jest wywoływana Between przetwarzanie komunikatów. Jednak w MFC bibliotek dołączanych dynamicznie (dll) `OnIdle()` funkcja nie jest wywoływana automatycznie. W rezultacie obiekty tymczasowe są nie automatycznie czyszczone. Aby wyczyścić obiekty tymczasowe, biblioteki DLL należy jawnie wywołać `OnIdle(1)` okresowo.

## <a name="see-also"></a>Zobacz też

[Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)