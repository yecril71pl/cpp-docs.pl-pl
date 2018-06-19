---
title: CUtlProps::OnInterfaceRequested | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CUtlProps
dev_langs:
- C++
helpviewer_keywords:
- OnInterfaceRequested method
ms.assetid: a5e1a879-cff3-4e01-b902-2249a152984f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 50a1f17294a91446e71a51ffdac6c5aec83f2c9a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099774"
---
# <a name="cutlpropsoninterfacerequested"></a>CUtlProps::OnInterfaceRequested
Obsługuje żądania dla interfejsu opcjonalny, gdy klient wywołuje metodę dla jednego obiektu Tworzenie interfejsów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      virtual HRESULT CUtlPropsBase::OnInterfaceRequested(REFIID riid);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 [in] Identyfikator IID dla żądanego interfejsu. Aby uzyskać więcej informacji, zobacz opis `riid` parametr `ICommand::Execute` w *OLE DB Podręcznik programisty* (w *MDAC SDK*).  
  
## <a name="remarks"></a>Uwagi  
 **OnInterfaceRequested** obsługuje żądania opcjonalny interfejs użytkownika, gdy klient wywołuje metodę dla jednego obiektu Tworzenie interfejsów (takich jak **IDBCreateSession**, **IDBCreateCommand**, `IOpenRowset`, lub `ICommand`). Ustawia odpowiednie właściwości OLE DB dla żądanego interfejsu. Na przykład, jeśli użytkownik zażąda **IID_IRowsetLocate**, **OnInterfaceRequested** ustawia **DBPROP_IRowsetLocate** interfejsu. Dzięki temu zachowuje stan podczas tworzenia zestawu wierszy.  
  
 Ta metoda jest wywoływana, gdy użytkownik wywołuje **IOpenRowset::OpenRowset** lub `ICommand::Execute`.  
  
 W przypadku klienta otwiera obiekt i żąda opcjonalny interfejs, dostawcy należy ustawić właściwość skojarzoną z tym interfejsem do `VARIANT_TRUE`. Aby zezwolić na przetwarzanie specyficzne dla właściwości **OnInterfaceRequested** jest wywoływana przed dostawcy **Execute** metoda jest wywoływana. Domyślnie **OnInterfaceRequested** obsługuje następujących interfejsów:  
  
-   `IRowsetLocate`  
  
-   `IRowsetChange`  
  
-   `IRowsetUpdate`  
  
-   **IConnectionPointContainer**  
  
-   `IRowsetScroll`  
  
 Jeśli chcesz obsługiwać inne interfejsy przesłonić tę funkcję w klasie źródła, sesji, poleceń lub zestawu wierszy danych do funkcji procesu. Zastąpienia powinien znajdować się za pośrednictwem interfejsów właściwości normalnego zestawu/get, aby upewnić się, że ustawienie właściwości określa również żadnych właściwości łańcuchowa (zobacz [OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [CUtlProps, klasa](../../data/oledb/cutlprops-class.md)