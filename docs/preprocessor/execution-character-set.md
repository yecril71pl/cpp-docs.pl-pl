---
title: execution_character_set | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- execution_character_set
- vc-pragma.execution_character_set
dev_langs:
- C++
helpviewer_keywords:
- pragma execution_character_set
ms.assetid: 32248cbc-7c92-4dca-8442-230c052b53ad
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eda04de6975708b2460e53681e50f8ea4f9dbcd3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="executioncharacterset"></a>execution_character_set
Określa zestaw znaków wykonania używane dla literałów ciągów i znakowe. Ta dyrektywa nie jest wymagany dla literałów oznaczone prefiksem u8.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma execution_character_set("target")  
```  
  
#### <a name="parameters"></a>Parametry  
 `target`  
 Określa zestaw znaków wykonania docelowej. Obecnie tylko wykonanie docelowego ustawić obsługiwane jest "utf-8".  
  
## <a name="remarks"></a>Uwagi  
 Ta dyrektywa kompilatora jest przestarzałe, począwszy od programu Visual Studio 2015 Update 2. Firma Microsoft zaleca użycie **/execution-charset:utf-8** lub **/UTF-8** — opcje kompilatora wraz z przy użyciu `u8` prefiks wąskie znaków i ciągu literałów zawierające rozszerzone znaki. Aby uzyskać więcej informacji na temat `u8` prefiksu, zobacz [literały ciągów i znakowe](../cpp/string-and-character-literals-cpp.md). Aby uzyskać więcej informacji na temat opcji kompilatora, zobacz [/Execution-Charset (Ustaw wykonywania zestaw znaków)](../build/reference/execution-charset-set-execution-character-set.md) i [/UTF-8 (Ustaw źródło i plik wykonywalny znak zestawów do UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md).  
  
 `#pragma execution_character_set("utf-8")` Dyrektywy informuje kompilator, aby zakodować literały wąski ciąg w kodzie źródłowym i znaki wąskie jako UTF-8 w pliku wykonywalnym. Ten typ kodowania danych wyjściowych jest niezależna od pliku źródłowego kodowanie używane.  
  
 Domyślnie kompilator koduje znaki wąskie i ciągi wąskie przy użyciu bieżącej strony kodowej jako zestaw znaków wykonania. Oznacza to, że znaki Unicode lub znaków Dwubajtowych w literału, które są poza zakresem bieżącej stronie kodowej są konwertowane na domyślnym znakiem zastępującym w danych wyjściowych. Znaki Unicode i znaków Dwubajtowych są zaokrąglane do ich mniej znaczącego bajtu. To jest prawie na pewno nie co ma. Można określić dla literałów w pliku źródłowym kodowania UTF-8 za pomocą `u8` prefiks. Kompilator przekazuje te ciągi kodowany w formacie UTF-8 bez zmian danych wyjściowych. Literały znaków wąskie prefiksem przy użyciu u8 musi mieścić się w jednego bajtu lub są one obcięte w danych wyjściowych.  
  
 Domyślnie program Visual Studio używa bieżącej stronie kodowej jako zestaw znaków źródła sposób interpretowania kodu źródłowego dla danych wyjściowych. Podczas odczytywania pliku w Visual Studio będą interpretowane przez go zgodnie z bieżącą stronę, chyba że określono strony kodowej plików lub znacznik kolejności bajtów (BOM) lub UTF-16 znaków, które zostaną wykryte na początku pliku. Ponieważ UTF-8 nie można ustawić jako bieżącej stronie kodowej, gdy automatyczne wykrywanie napotka zakodowane jako UTF-8 bez BOM pliki źródłowe, Visual Studio zakłada, że są zakodowane przy użyciu bieżącej strony kodowej. Znaki w pliku źródłowym, które są poza zakresem określonym lub automatycznie wykrył, że strona kodowa może spowodować kompilatora ostrzeżeń i błędów.  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [/ Execution-Charset (Ustaw wykonywania zestaw znaków)](../build/reference/execution-charset-set-execution-character-set.md)   
 [/utf-8 (Ustaw źródłowy i wykonywalny zestaw znaków na UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)