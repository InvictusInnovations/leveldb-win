set( sources 
    db/builder.cc
    db/c.cc
#    db/db_bench.cc
    db/db_impl.cc
    db/db_iter.cc
    db/dbformat.cc
    db/filename.cc
#    db/leveldb_main.cc
    db/log_reader.cc
    db/log_writer.cc
    db/memtable.cc
    db/repair.cc
    db/table_cache.cc
    db/version_edit.cc
    db/version_set.cc
    db/write_batch.cc

#    port/port_posix.cc
    port/port_win.cc

    helpers/memenv/memenv.cc

    util/arena.cc
#na    util/bloom.cc
    util/cache.cc
    util/coding.cc
    util/comparator.cc
    util/crc32c.cc
    util/env.cc
	util/env_boost.cc
	util/win_logger.cc
#    util/env_posix.cc
#na    util/filter_policy.cc
    util/hash.cc
    util/histogram.cc
    util/logging.cc
    util/options.cc
    util/status.cc

    table/block.cc
    table/block_builder.cc
#na    table/filter_block.cc
    table/format.cc
    table/iterator.cc
    table/merger.cc
    table/table.cc
    table/table_builder.cc
    table/two_level_iterator.cc
)

add_library( leveldb  ${sources} )

target_include_directories(leveldb 
  PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include
  PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}
  PRIVATE ${Boost_INCLUDE_DIR}
  )

IF(WIN32)
  target_compile_definitions(leveldb PUBLIC LEVELDB_PLATFORM_WINDOWS PRIVATE OS_WIN BOOST_ALL_NO_LIB)
  # see fc CMakeLists.txt for details
  target_compile_options(leveldb PUBLIC /EHsc /UBOOST_ALL_DYN_LINK /UBOOST_LINKING_PYTHON /UBOOST_DEBUG_PYTHON)
ENDIF(WIN32)

