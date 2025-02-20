cmake_minimum_required (VERSION 2.6)
project (protocol)

set(SOURCES
		amcp/AMCPCommandQueue.cpp
		amcp/AMCPCommandsImpl.cpp
		amcp/AMCPProtocolStrategy.cpp
		amcp/amcp_command_repository.cpp

		cii/CIICommandsImpl.cpp
		cii/CIIProtocolStrategy.cpp

		clk/CLKProtocolStrategy.cpp
		clk/clk_commands.cpp
		clk/clk_command_processor.cpp

		log/tcp_logger_protocol_strategy.cpp

		osc/oscpack/OscOutboundPacketStream.cpp
		osc/oscpack/OscPrintReceivedElements.cpp
		osc/oscpack/OscReceivedElements.cpp
		osc/oscpack/OscTypes.cpp

		osc/client.cpp

		util/AsyncEventServer.cpp
		util/lock_container.cpp
		util/strategy_adapters.cpp

		StdAfx.cpp
)
set(HEADERS
		amcp/AMCPCommand.h
		amcp/AMCPCommandQueue.h
		amcp/AMCPCommandsImpl.h
		amcp/AMCPProtocolStrategy.h
		amcp/amcp_command_repository.h
		amcp/amcp_shared.h

		cii/CIICommand.h
		cii/CIICommandsImpl.h
		cii/CIIProtocolStrategy.h

		clk/CLKProtocolStrategy.h
		clk/clk_commands.h
		clk/clk_command_processor.h

		log/tcp_logger_protocol_strategy.h

		osc/oscpack/MessageMappingOscPacketListener.h
		osc/oscpack/OscException.h
		osc/oscpack/OscHostEndianness.h
		osc/oscpack/OscOutboundPacketStream.h
		osc/oscpack/OscPacketListener.h
		osc/oscpack/OscPrintReceivedElements.h
		osc/oscpack/OscReceivedElements.h
		osc/oscpack/OscTypes.h

		osc/client.h

		util/AsyncEventServer.h
		util/ClientInfo.h
		util/lock_container.h
		util/ProtocolStrategy.h
		util/protocol_strategy.h
		util/strategy_adapters.h

		StdAfx.h
)

add_library(protocol ${SOURCES} ${HEADERS})
add_precompiled_header(protocol StdAfx.h FORCEINCLUDE)

include_directories(..)
include_directories(${BOOST_INCLUDE_PATH})
include_directories(${RXCPP_INCLUDE_PATH})
include_directories(${TBB_INCLUDE_PATH})

source_group(sources\\amcp amcp/*)
source_group(sources\\cii cii/*)
source_group(sources\\clk clk/*)
source_group(sources\\log log/*)
source_group(sources\\osc\\oscpack osc/oscpack/*)
source_group(sources\\osc osc/*)
source_group(sources\\util util/*)
source_group(sources ./*)

target_link_libraries(protocol common core reroute)
