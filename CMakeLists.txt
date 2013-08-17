include_directories( ${CMAKE_CURRENT_SOURCE_DIR}/include )
include_directories( ${CMAKE_CURRENT_SOURCE_DIR} )

IF(WIN32)
  ADD_DEFINITIONS( -DLEVELDB_PLATFORM_WINDOWS)
  ADD_DEFINITIONS( -DOS_WIN)
ENDIF(WIN32)

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
