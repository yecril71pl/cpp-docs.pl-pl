---
title: pgomgr | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8cbb9a4f8b92a1cd495e1312c1aa8a8f77cefcd3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="pgomgr"></a>pgomgr
Dodaje dane profilu z jednego lub więcej plików .pgc do plik .pgd.  
  
## <a name="syntax"></a>Składnia  
  
```  
pgomgr [options] pgcfiles pgdfile  
```  
  
#### <a name="parameters"></a>Parametry  
 `options`  
 Aby pgomgr można określić następujące opcje:  
  
 **/ help —**Wyświetla opcje dostępne pgomgr (skrót /?).  
  
 **/ clear-**powoduje, że plik .pgd do wyczyszczenia wszystkich danych profilu. Nie można określić .pgc plików podczas **/clear** jest określona.  
  
 **/ detail**— Wyświetla szczegółowe statystyki, w tym informacje o pokryciu Wykres przepływu.  
  
 **/ summary**— wyświetla na funkcji statystyk.  
  
 **/ unique**— w przypadku użycia z **/summary**, przyczyny dekorowane nazwy funkcji do wyświetlenia.  Domyślnie, gdy / jest unikatowy nie jest używana, jest dla nazwy funkcji bez mają być wyświetlane.  
  
 **/ merge**[**:***n*]**—**powoduje, że dane w pliku .pgc lub pliki, które mają zostać dodane do pliku .pgd.  Opcjonalny parametr  *n* , pozwala określić hat dane powinny zostać dodane  *n*  razy.  Na przykład, jeśli scenariusz często będą wykonywane 6 razy, można odbywa się raz w uruchomienia testu i dodaj go do pliku .pgd sześć razy z **pgomgr /merge:6**.  
  
 `pgcfiles`  
 Co najmniej jeden .pgc pliki danych profilu, którego chcesz scalić plik .pgd. Można określić plik .pgc jednego lub wielu plików .pgc. Jeśli nie określono żadnych plików .pgc, pgomgr scali wszystkie pliki .pgc, których nazwy plików są takie same jak plik .pgd.  
  
 `pgdfile`  
 Plik .pgd, do którego są scalane dane z pliku .pgc lub plików.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Można uruchomić to narzędzie tylko z [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] wiersza polecenia. Nie można uruchomić go z wiersza polecenia systemu lub z Eksploratora plików.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie plik .pgd został wyczyszczony danych profilu.  
  
```  
pgomgr /clear myapp.pgd  
```  
  
 W poniższym przykładzie danych profilu w myapp1.pgc zostało dodane do pliku .pgd 3 razy.  
  
```  
pgomgr /merge:3 myapp1.pgc myapp.pgd  
```  
  
 W poniższym przykładzie danych profilu z wszystkie pliki # .pgc moja_aplikacja są dodawane do pliku myapp.pgd.  
  
```  
pgomgr -merge myapp1.pgd  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia do ręcznej optymalizacji sterowanej profilem](../../build/reference/tools-for-manual-profile-guided-optimization.md)