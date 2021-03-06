set(LLVM_TARGET_DEFINITIONS XCore.td)

tablegen(LLVM XCoreGenRegisterInfo.inc -gen-register-info)
tablegen(LLVM XCoreGenInstrInfo.inc -gen-instr-info)
tablegen(LLVM XCoreGenDisassemblerTables.inc -gen-disassembler)
tablegen(LLVM XCoreGenAsmWriter.inc -gen-asm-writer)
tablegen(LLVM XCoreGenDAGISel.inc -gen-dag-isel)
tablegen(LLVM XCoreGenCallingConv.inc -gen-callingconv)
tablegen(LLVM XCoreGenSubtargetInfo.inc -gen-subtarget)
add_public_tablegen_target(XCoreCommonTableGen)

add_llvm_target(XCoreCodeGen
  XCoreAsmPrinter.cpp
  XCoreFrameLowering.cpp
  XCoreInstrInfo.cpp
  XCoreISelDAGToDAG.cpp
  XCoreISelLowering.cpp
  XCoreLowerThreadLocal.cpp
  XCoreMachineFunctionInfo.cpp
  XCoreMCInstLower.cpp
  XCoreRegisterInfo.cpp
  XCoreSubtarget.cpp
  XCoreTargetMachine.cpp
  XCoreTargetObjectFile.cpp
  XCoreSelectionDAGInfo.cpp
  XCoreFrameToArgsOffsetElim.cpp
  )

add_subdirectory(Disassembler)
add_subdirectory(InstPrinter)
add_subdirectory(TargetInfo)
add_subdirectory(MCTargetDesc)
