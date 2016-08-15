# Sorted Tab History

![travis-ci](https://travis-ci.org/kataho/tab-history-mrx.svg?branch=master)

Yet another tab item manager which sorts tabs with elapsed time from various things done recently.

This Atom package provides a list of tabs in each pane which is ordered by elapsed time from various user actions
(save, modification, cursor move and tab activation for now).
Of course also provides commands for keymap to navigate among the list.

Many editors have back/forward navigation feature, meanwhile, there is a small difference between
way of ordering items. It represents no ideal one in this world.
Finding the best of your own is the main point of this package.

< picture here >

## Keymap Commands

**Back**  - Activate previous (older) item of current active item in the history

**Forward** - Activate next (newer) item of current active item in the history

**Top** - Activate the most recent item in the history

## Options

#### Ranks of Sort Priority

The history is sorted by multiple factors. First, tab items are sorted with time from last action of the best rank,
and on a subset of items with too old to compare, another sort is applied with time from last action of second best rank, and so forth.

\* The rank -1 means disabled. The action is ignored.

**Sort Rank : Internal Select** - Sorting priority rank of activation of a tab item (by this package feature)

**Sort Rank : External Select** - Sorting priority rank of activation of a tab item (by other tab item selecting feature)

**Sort Rank : Cursor Move** - Sorting priority rank of cursor move on an editor

**Sort Rank : Change** - Sorting priority rank of content change of an editor

**Sort Rank : Save** - Sorting priority rank of save of content of a tab item

#### Expiration of Event History

Integer of minutes of an action expires. An expired action is handled as never occurred.
It causes a next lower rank action to be picked to decide an order of the tab item.

\* An action labelled as the lowest rank among enabled ranks never expires.

#### Tab Auto Closing

Number of tabs we attempt to keep in a pane. a bottom item in the history list is used as a candidate to be closed in exchange for an item being added.

## Setting Samples

#### Most Recently Activated

The List of recently used items; very common rule of sorting.

    SortRank:InternalSelect = -1
    SortRank:ExternalSelect = 1
    SortRank:Cursor = -1
    SortRank:Change = -1
    SortRank:Save = -1

Selecting from this activation history also changes history.

    SortRank:InternalSelect = 1
    SortRank:ExternalSelect = 1
    SortRank:Cursor = -1
    SortRank:Change = -1
    SortRank:Save = -1

Preventing changed item to be auto closed.

    SortRank:InternalSelect = 1
    SortRank:ExternalSelect = 1
    SortRank:Cursor = -1
    SortRank:Change = 2
    SortRank:Save = -1
    ExpirationOfEvents = 5
