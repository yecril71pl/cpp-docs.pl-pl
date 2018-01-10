---
title: "Porady: migracji do środowiska clr-: pure (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- /clr compiler option [C++], migrating to /clr:pure
- migration [C++], pure MSIL
- pure MSIL [C++], porting to
ms.assetid: 5ffb1184-2095-4ade-84aa-4fa6324bc764
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b8d49ee233167c02570408ba091c2a99b78487d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-migrate-to-clrpure-ccli"></a>Porady: migracja do /clr:pure (C++/CLI)
W tym temacie omówiono problemy mogą wystąpić podczas migracji do czysty MSIL przy użyciu **/CLR: pure** (zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md) Aby uzyskać więcej informacji). W tym temacie założono kodu migrowane obecnie zgodności jako mieszanego zestawu za pomocą **/CLR** opcję jako ścieżki migracji z kodem niezarządzanym do czysty MSIL nie jest elementem bezpośredniego. Dla niezarządzanego kodu, zobacz [porady: Migracja do/CLR](../dotnet/how-to-migrate-to-clr.md) przed przystąpieniem do migracji do czysty MSIL.  
  
## <a name="basic-changes"></a>Zmiany podstawowego  
 Czysty MSIL składa się z instrukcjami MSIL, więc kod zawierający funkcje, których nie można wyrazić w MSIL uniemożliwi kompilacji. Dotyczy to również funkcji definiowanych jako inny niż przy użyciu konwencji wywoływania [__clrcall](../cpp/clrcall.md). (Funkcji __clrcall z systemem innym niż mogą być wywoływane w składniku czysty MSIL, ale nie zdefiniowano).  
  
 Aby zapewnić bez błędów czasu wykonywania, należy włączyć ostrzeżenie C4412. Włączanie C4412 przez dodanie `#pragma warning (default : 4412)` do każdego compiland, który kompilacji z **/CLR: pure** i przekazanie typy C++ do i z IJW (**/CLR)** lub kodu natywnego. Zobacz [C4412 ostrzeżenie kompilatora (poziom 2)](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md) Aby uzyskać więcej informacji.  
  
## <a name="architectural-considerations"></a>Zagadnienia dotyczące architektury  
 Niektóre ograniczenia wymienione w zestawy czyste MSIL [czystej i weryfikowalny kod (C + +/ CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md) wysokiego poziomu dotyczą strategii projektowania i migracji aplikacji. Głównie w przeciwieństwie do zestawów mieszanych zestawy czyste MSIL nie korzystać z pełnej zgodności z modułami niezarządzane.  
  
 Zestawy czyste MSIL wywołaniem funkcji niezarządzane, ale nie można wywołać za pomocą funkcji niezarządzanej. W związku z tym czysty MSIL jest lepsze kandydatem do kodu klienta, który używa niezarządzanej funkcji niż kod serwera, który jest używany przez funkcje niezarządzane. W przypadku funkcji zawartych w zestawie czysty MSIL do użycia przez funkcje niezarządzane, należy użyć mieszanego zestawu jako warstwy interfejsu.  
  
 Aplikacje używające ATL ani MFC nie są odpowiednimi obiektami do migracji do czysty MSIL jako biblioteki te nie są obsługiwane w tej wersji. Podobnie [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)] zawiera pliki nagłówkowe, nie kompilowane w obszarze **/CLR: pure**.  
  
 Podczas zestawy czyste MSIL wywołaniem funkcji niezarządzanej ta możliwość jest ograniczona do proste funkcje w stylu języka C. Korzystanie z bardziej złożonych niezarządzane interfejsy API jest mogących wymagać niezarządzanych funkcji mają być uwidaczniane w postaci interfejsu COM lub mieszanego zestawu, który może działać jako interfejs między czysty MSIL i składniki niezarządzane. Za pomocą warstwy mieszanego zestawu jest jedynym sposobem, aby użyć niezarządzanych funkcji, które przyjmują funkcje wywołania zwrotnego, na przykład jako czysty zestawu nie może dostarczyć można wywołać funkcji natywnej do użycia jako wywołanie zwrotne.  
  
## <a name="application-domains-and-calling-conventions"></a>Domeny aplikacji i Konwencje wywoływania  
 Chociaż można dla czysty MSIL zestawy używać funkcji niezarządzane, funkcje i dane statyczne są obsługiwane w inny sposób. W zestawach czystej funkcji są implementowane przy użyciu [__clrcall](../cpp/clrcall.md) wywoływanie Konwencji, a dane statyczne jest przechowywane domeny dla poszczególnych aplikacji. Różni się to z domyślnego dla zestawów niezarządzane i mieszanych, korzystających z [__cdecl](../cpp/cdecl.md) konwencji wywoływania funkcji i przechowywania danych statycznych w zasadzie na proces.  
  
 W kontekście czysty MSIL (i możliwe do zweryfikowania kodu skompilowanego za pomocą/CLR: Safe) te wartości domyślne są niewidoczne, jako [__clrcall](../cpp/clrcall.md) jest Konwencja wywoływania domyślnego środowiska CLR i domen aplikacji natywnej zakres statyczne i dane globalne w aplikacjach .NET. Jednak gdy relacje z niezarządzanych lub mieszane składników, różne traktowanie funkcji i danych globalnych może powodować problemy.  
  
 Na przykład jeśli składnik czysty MSIL wywoływać funkcje w zarządzaniu lub mieszane biblioteki DLL, pliku nagłówka dla biblioteki DLL będzie służyć do skompilowania czysty zestawu. Jednak inaczej Konwencja wywoływania dla poszczególnych funkcji w nagłówku jest jawnie, one będą wszystkie zakłada się, że można [__clrcall](../cpp/clrcall.md). Później spowoduje to błędy czasu wykonywania, ponieważ te funkcje są prawdopodobnie wykonywane przy [__cdecl](../cpp/cdecl.md) Konwencji. Funkcje w pliku nagłówka niezarządzane może być jawnie oznaczony jako [__cdecl](../cpp/cdecl.md), lub cały kod źródłowy DLL musi być ponownie kompilowane w obszarze **/CLR: pure**.  
  
 Podobnie, wskaźniki funkcji uznaje się, że polecenie [__clrcall](../cpp/clrcall.md) funkcji w obszarze **/CLR: pure** kompilacji. Te zbyt musi być jawnie adnotowany przy poprawne konwencję wywołania.  
  
 Aby uzyskać więcej informacji, zobacz [i domen aplikacji Visual C++](../dotnet/application-domains-and-visual-cpp.md).  
  
## <a name="linking-limitations"></a>Ograniczenia łączenia  
 Konsolidatora Visual C++ nie będzie próbował połączyć mieszanych i czysty pliki OBJ jako magazynu zakresu i wywoływanie Konwencji są różne.  
  
## <a name="see-also"></a>Zobacz też  
 [Kod czysty i weryfikowalny (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)