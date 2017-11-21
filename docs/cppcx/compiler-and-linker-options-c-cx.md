---
title: Opcje kompilatora i konsolidatora (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecfadce8-3a3f-40cc-bb01-b4731f8d2fcb
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 868e167e68cf2fba6a8252ba390ab73268a78005
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-and-linker-options-ccx"></a>Opcje kompilatora i konsolidatora (C + +/ CX)
Wartość zmiennej środowiskowej, C + +/ CX — opcje kompilatora i opcje konsolidatora obsługuje tworzenie aplikacji dla środowiska uruchomieniowego systemu Windows.  
  
## <a name="library-path"></a>Ścieżka biblioteki  
 % Libpath-zmienna środowiskowa % ścieżka domyślna do wyszukiwania plików winmd.  
  
## <a name="compiler-options"></a>Opcje kompilatora  
  
|Opcja|Opis|  
|------------|-----------------|  
|[/ZW](../build/reference/zw-windows-runtime-compilation.md)<br /><br /> /Zw:nostdlib|Włącza rozszerzenia języka środowiska uruchomieniowego systemu Windows.<br /><br /> `nostdlib` Parametr zapobiega kompilatora przy użyciu ścieżki wyszukiwania standardowych, wstępnie zdefiniowanych można znaleźć plików zestawu i winmd.<br /><br /> **/ZW** — opcja kompilatora określa niejawnie następujących opcji kompilatora:<br /><br /> -   **/Fi** vccorlib.h, która wymusza włączenia vccorlib.h pliku nagłówka, który definiuje wiele typów, które są wymagane przez kompilator.<br />-   [/Fu](../build/reference/fu-name-forced-hash-using-file.md) plik Windows.winmd, który wymusza włączenia jego pliku metadanych plik Windows.winmd jest udostępniany przez system operacyjny, który definiuje wiele typów w środowisku wykonawczym systemu Windows.<br />-   **/Fu** Platform.winmd, która wymusza dołączania jest świadczona przez kompilator, który definiuje większość typów z nazw rodziny platformy pliku metadanych Platform.winmd.|  
|[/AI](../build/reference/ai-specify-metadata-directories.md) *dir*|Dodaje katalog, który jest określony przez *dir* parametru do ścieżki wyszukiwania używające przez kompilator w celu znalezienia plików zestawu i winmd.|  
|**/Fu***pliku* |Powoduje włączenie określonym module lub plik winmd. Oznacza to, że nie trzeba określić `#using` *pliku* w kodzie źródłowym. Kompilator automatycznie wymusza włączenia własny plik metadanych systemu Windows Platform.winmd.|  
|/D "WINAPI_FAMILY = 2"|Tworzy definicję, która umożliwia korzystanie z podzestawu Win32 SDK, który jest zgodny z środowiska uruchomieniowego systemu Windows.|  
  
## <a name="linker-options"></a>Opcje konsolidatora  
  
|Opcja|Opis|  
|------------|-----------------|  
|/ APPCONTAINER [: NO]|Oznacza plik wykonywalny jako do uruchomienia w kontenerze appcontainer (tylko).|  
|/ WINMD [: {NO &#124; TYLKO}]|Emituje plik winmd i skojarzony plik binarny. Ta opcja muszą być przekazywane do konsolidatora dla winmd, aby emitować.<br /><br /> **NIE**— nie emituj pliku winmd, ale Emituj pliku binarnego.<br /><br /> **TYLKO**— emituje plik winmd, ale nie emituj pliku binarnego.|  
|/ WINMDFILE:*filename*|Nazwa pliku winmd do emisji, zamiast domyślnej nazwy pliku winmd. Jeśli w wierszu polecenia określono wiele nazw plików, nazwisko jest używany.|  
|/ WINMDDELAYSIGN [: NO]|Częściowo podpisuje plik winmd i umieszczenie klucza publicznego w danych binarnych.<br /><br /> **NIE**—(Default) nie podpisać plik winmd.<br /><br /> / WINMDDELAYSIGN nie ma znaczenia, chyba że /WINMDKEYFILE lub /WINMDKEYCONTAINER jest określona.|  
|/ WINMDKEYCONTAINER:*nazwa*|Określa klucz kontenera, aby podpisać zestaw. *Nazwa* parametr odnosi się do kontenera klucza, który jest używany do podpisywania pliku metadanych.|  
|/ WINMDKEYFILE:*filename*|Określa klucz lub parę kluczy, aby podpisać zestaw. *Filename* parametru odpowiada klucz, który jest używany do podpisywania pliku metadanych.|  
  
### <a name="remarks"></a>Uwagi  
 Jeśli używasz **/ZW**, kompilator automatycznie łączy się wersja biblioteki DLL z C Runtime (CRT). Łączenie wersji biblioteki statycznej nie jest dozwolone, a użycia funkcji CRT, które nie są dozwolone w aplikacji platformy uniwersalnej systemu Windows spowoduje błąd w czasie kompilacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie aplikacji i biblioteki](../cppcx/building-apps-and-libraries-c-cx.md)