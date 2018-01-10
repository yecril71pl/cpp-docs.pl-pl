---
title: __fastfail | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 9cd32639-e395-4c75-9f3a-ac3ba7f49921
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: efdd067376d8e1430ed8636c0a77afe950858e9a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fastfail"></a>__fastfail
**Dotyczące firmy Microsoft**  
  
 Natychmiast kończy proces wywoływania co najmniej obciążenie.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __fastfail(unsigned int code);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`code`  
 A `FAST_FAIL_<description>` stała symboliczne z pliku winnt.h lub wdm.h wskazujący przyczynę Kończenie procesu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `__fastfail` Wewnętrznej nie zwraca.  
  
## <a name="remarks"></a>Uwagi  
 `__fastfail` Wewnętrzne udostępnia mechanizm *szybkie niepowodzenie* żądania — sposób potencjalnie uszkodzony procesu zakończenia procesu natychmiastowego żądania. Błędy krytyczne, które mogą mieć uszkodzony stan programu i stosu poza odzyskiwania nie mogą być obsługiwane przez regularne obsługi zakładzie wyjątków. Użyj `__fastfail` zakończenie procesu przy użyciu minimalnego obciążenia.  
  
 Wewnętrznie `__fastfail` jest implementowane za pomocą kilka mechanizmów architektury:  
  
|Architektura|Instrukcja|Lokalizacja kodu argumentu|  
|------------------|-----------------|-------------------------------|  
|x86|int 0x29|ECx|  
|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|int 0x29|rcx|  
|ARM|Kod operacji 0xDEFB|r0|  
  
 Żądanie szybkiego błędów jest niezależna i zwykle wymaga dwóch instrukcje do wykonania. Gdy żądanie szybkiego błędów zostało wykonane jądra następnie podejmuje odpowiednie działanie. W kodzie trybu użytkownika nie ma żadnych zależności pamięci poza się wskaźnik instrukcji, przypadku zdarzenia szybkiego kończyć się niepowodzeniem. Maksymalizuje wiarygodność, nawet jeśli pamięci poważne uszkodzenie.  
  
 `code` Argument — jeden z `FAST_FAIL_<description>` stałe symboliczne z pliku winnt.h lub wdm.h—describes typ stanu błędu i jest włączony do raportów o awarii w sposób określonego środowiska.  
  
 Tryb użytkownika szybkiego Niepowodzenie żądania są wyświetlane jako drugiej szansy kontynuację wyjątek z kod wyjątku 0xC0000409 i wyjątek co najmniej jeden parametr. Pierwszy parametr wyjątku ma `code` wartość. Ten kod wyjątku wskazuje raportowania błędów systemu Windows (WER) i debugowania infrastruktury, że proces jest uszkodzony, a minimalny w trakcie działania należy podjąć w odpowiedzi na awarię. Trybu jądra szybkiego Niepowodzenie żądania są implementowane przy użyciu kodu dedykowanych operacji wykrywania błędów, `KERNEL_SECURITY_CHECK_FAILURE` (0x139). W obu przypadkach nie programy obsługi wyjątków są wywołać, ponieważ program powinien być w stanie uszkodzenia. Jeśli jest obecny debuger, otrzymuje możliwość sprawdzenia stanu programu przed zakończeniem działania.  
  
 Obsługa mechanizmu natywnego niepowodzenie szybkiego zostało uruchomione w systemie Windows 8. Systemów operacyjnych Windows, które nie obsługują natywnie instrukcji szybkiego niepowodzenie zazwyczaj traktują żądanie szybkiego niepowodzenie naruszenia zasad dostępu lub jako `UNEXPECTED_KERNEL_MODE_TRAP` wyniki operacji. W takich przypadkach program jest nadal zakończone, ale niekoniecznie tak szybko.  
  
 `__fastfail`jest dostępna jako funkcja wewnętrzna tylko.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__fastfail`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)], ARM|  
  
 **Plik nagłówka** \<intrin.h >  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)