---
title: ICLRDebugging::OpenVirtualProcess – metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugging.OpenVirtualProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51b5a9ecd85f0d40ac2fe2826cbbe7a56a6228d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408249"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a>ICLRDebugging::OpenVirtualProcess – metoda
Získá rozhraní ICorDebugProcess, která odpovídá common language runtime (CLR) modul načíst v procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OpenVirtualProcess(  
    [in] ULONG64 moduleBaseAddress,  
    [in] IUnknown * pDataTarget,  
    [in] ICLRDebuggingLibraryProvider * pLibraryProvider,  
    [in] CLR_DEBUGGING_VERSION * pMaxDebuggerSupportedVersion,  
    [in] REFIID riidProcess,  
    [out, iid_is(riidProcess)] IUnknown ** ppProcess,  
    [in, out] CLR_DEBUGGING_VERSION * pVersion,  
    [out] CLR_DEBUGGING_PROCESS_FLAGS * pdwFlags);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleBaseAddress`  
 [v] Základní adresa modulu v tento cílový proces. COR_E_NOT_CLR bude vrácen, pokud zadaný modul není modulu CLR.  
  
 `pDataTarget`  
 [v] Abstrakce cílový data, která umožňuje spravované ladicí program ke kontrole stavu procesu. Ladicí program musí implementovat [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní. Měli byste implementovat [iclrdebugginglibraryprovider –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) rozhraní podporu scénářů, kde není CLR, který je právě laděn nainstalovaná místně v počítači.  
  
 `pLibraryProvider`  
 [v] Rozhraní zpětné volání zprostředkovatele knihovny, které lze najít a načíst na vyžádání specifické pro verzi ladění knihoven. Tento parametr je vyžadován, pouze pokud `ppProcess` nebo `pFlags` není `null`.  
  
 `pMaxDebuggerSupportedVersion`  
 [v] Nejvyšší verze modulu CLR, který můžete ladit tento ladicí program. By měl určit hlavní, vedlejší verzi a vytvářet verze z nejnovější verze CLR, kterou podporuje tento ladicí program a nastavte číslo revize do 65535, aby dokázala pojmout budoucí CLR místní obsluhy verze.  
  
 `riidProcess`  
 [v] ID rozhraní ICorDebugProcess k načtení. V současné době jsou pouze hodnoty IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 a IID_CORDEBUGPROCESS.  
  
 `ppProcess`  
 [out] Ukazatel na rozhraní modelu COM, která je identifikovaná `riidProcess`.  
  
 `pVersion`  
 [ve out] Verze modulu CLR. Na vstupu, tato hodnota může být `null`. Může taky ukazovat na [clr_debugging_version –](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) struktury v takovém případě struktura `wStructVersion` pole musí být inicializován na hodnotu 0 (nula).  
  
 Na výstupu vráceného `CLR_DEBUGGING_VERSION` struktura se uvede informace o verzi modulu CLR.  
  
 `pdwFlags`  
 [out] Informační příznaky o zadaného modulu runtime. Najdete v článku [CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) tématu Popis příznaků.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pDataTarget` je `null`.|  
|CORDBG_E_LIBRARY_PROVIDER_ERROR|[Iclrdebugginglibraryprovider –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) zpětného volání vrátí chybu nebo neposkytuje platný popisovač.|  
|CORDBG_E_MISSING_DATA_TARGET_INTERFACE|`pDataTarget` neimplementuje rozhraní target požadovaných dat pro tuto verzi modulu runtime.|  
|CORDBG_E_NOT_CLR|Modul uvedené není modulu CLR. Tato HRESULT je také vrácena, pokud modul CLR nelze nalézt, protože byl poškozen paměti, modul není k dispozici nebo CLR verze je novější než verze shim.|  
|CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL|Tato verze modulu runtime nepodporuje tento ladění model. V současné době ladění modelu není podporována verze CLR před [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. `pwszVersion` Výstupní parametr je stále nastavené na správnou hodnotu po této chybě.|  
|CORDBG_E_UNSUPPORTED_FORWARD_COMPAT|Je větší než verze, kterou tento ladicí program deklarace identity pro podporu verzi modulu CLR. `pwszVersion` Výstupní parametr je stále nastavené na správnou hodnotu po této chybě.|  
|E_NO_INTERFACE|`riidProcess` Rozhraní není k dispozici.|  
|CORDBG_E_UNSUPPORTED_VERSION_STRUCT|`CLR_DEBUGGING_VERSION` Struktura nemá platný hodnotu `wStructVersion`. Jediná hodnota přijaté v tuto chvíli je 0.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
