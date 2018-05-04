---
title: Przykłady skryptów rejestru | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c192e8bec1d32dd7d7a7953e5da72a139c7520e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="registry-scripting-examples"></a>Przykłady skryptów rejestru
Przykłady skryptów w tym temacie przedstawiają sposób Dodaj klucz do rejestru systemowego, Zarejestruj serwer COM rejestratora i określ wiele drzewa analizy.  
  
## <a name="add-a-key-to-hkeycurrentuser"></a>Dodaje klucz do HKEY_CURRENT_USER  
 Następujące drzewo analizy przedstawiono prosty skrypt, który dodaje jednego klucza do rejestru systemowego. W szczególności skrypt dodaje klucz, `MyVeryOwnKey`, do `HKEY_CURRENT_USER`. Przypisuje także wartość ciągu domyślne `HowGoesIt` do nowego klucza:  
  
```  
HKEY_CURRENT_USER  
{  
 'MyVeryOwnKey' = s 'HowGoesIt'  
}  
```  
  
 Ten skrypt można z łatwością rozszerzyć do definiowania wielu podkluczy w następujący sposób:  
  
```  
HKCU  
{  
 'MyVeryOwnKey' = s 'HowGoesIt'  
 {  
 'HasASubkey'  
 {  
 'PrettyCool' = d '55'  
    val 'ANameValue' = s 'WithANamedValue'  
 }  
 }  
}  
```  
  
 Teraz, skrypt ten dodaje podklucz, `HasASubkey`, do `MyVeryOwnKey`. Do tego podklucza dodaje zarówno `PrettyCool` podklucz (domyślnie `DWORD` wartość 55) i `ANameValue` o nazwie wartość (o wartości ciągu `WithANamedValue`).  
  
##  <a name="_atl_register_the_registrar_com_server"></a> Zarejestruj serwer COM rejestratora  
 Poniższy skrypt rejestruje sam serwer COM rejestratora.  
  
```  
HKCR  
{  
    ATL.Registrar = s 'ATL Registrar Class'  
 {  
    CLSID = s '{44EC053A-400F-11D0-9DCD-00A0C90391D3}'  
 }  
    NoRemove CLSID  
 {  
    ForceRemove {44EC053A-400F-11D0-9DCD-00A0C90391D3} = 
    s 'ATL Registrar Class'  
 {  
    ProgID = s 'ATL.Registrar'  
    InprocServer32 = s '%MODULE%'  
 {  
    val ThreadingModel = s 'Apartment'  
 }  
 }  
 }  
}  
```  
  
 W czasie wykonywania, dodaje tego drzewa analizy `ATL.Registrar` klucza `HKEY_CLASSES_ROOT`. Do tego nowego klucza następnie it:  
  
-   Określa `ATL Registrar Class` klucza domyślną wartość ciągu.  
  
-   Dodaje `CLSID` jako podklucz.  
  
-   Określa `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` dla `CLSID`. (Ta wartość jest rejestratorem CLSID do użycia z `CoCreateInstance`.)  
  
 Ponieważ `CLSID` jest udostępnione, jego nie powinny być usuwane w trybie Unregister. Instrukcja `NoRemove CLSID`, przez co oznacza, że `CLSID` powinny być otwierane w trybie rejestrowania i zignorowane w trybie Unregister.  
  
 `ForceRemove` Instrukcji udostępnia funkcję celów przez usunięcie klucza i wszystkich jego podkluczy przed ponowne tworzenie klucza. Może to być przydatne, jeśli nazwy podkluczy zostały zmienione. W tym przykładzie skryptów `ForceRemove` sprawdza, czy `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` już istnieje. Jeśli tak, `ForceRemove`:  
  
-   Usuwa rekursywnie `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` i wszystkich jego podkluczy.  
  
-   Ponownie tworzy `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.  
  
-   Dodaje `ATL Registrar Class` jako domyślną wartość ciągu dla `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.  
  
 W drzewie analizy teraz dodaje dwa nowe podklucze do `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`. Pierwszy klucz `ProgID`, pobiera domyślną wartość ciągu, która jest identyfikator ProgID. Drugi klucz `InprocServer32`, pobiera wartość domyślną ciąg `%MODULE%`, która jest wartość preprocesora wyjaśniono w sekcji [przy użyciu parametry wymienne (Rejestrator preprocesora)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md), tego artykułu. `InprocServer32` pobiera również wartość nazwanego `ThreadingModel`, z wartością ciągu `Apartment`.  
  
## <a name="specify-multiple-parse-trees"></a>Określ wiele drzewa analizy  
 Aby określić więcej niż jeden drzewo analizy w skrypcie, po prostu umieść jednym drzewie na końcu innego. Na przykład poniższy skrypt dodaje klucz, `MyVeryOwnKey`, do drzewa analizy dla obu `HKEY_CLASSES_ROOT` i `HKEY_CURRENT_USER`:  
  
```  
HKCR  
{  
 'MyVeryOwnKey' = s 'HowGoesIt'  
}  
HKEY_CURRENT_USER  
{  
 'MyVeryOwnKey' = s 'HowGoesIt'  
}  
```  
  
> [!NOTE]
>  W przypadku skryptu rejestratora 4K jest maksymalny rozmiar tokenu. (Token jest dowolny element rozpoznawalną w składni). W poprzednim przykładzie skryptów `HKCR`, `HKEY_CURRENT_USER`, `'MyVeryOwnKey'`, i `'HowGoesIt'` są wszystkie tokeny.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie skryptów rejestratora](../atl/creating-registrar-scripts.md)

