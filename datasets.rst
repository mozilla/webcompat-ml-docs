********
Datasets
********

Our dataset is based in the `webcompat <https://webcompat.com>`_ GitHub issues submitted on `webcompat/web-bugs <https://github.com/webcompat/web-bugs>`_.
In order to build the dataset we used the GitHub API and specifically the following endpoints:

* `List issues for a repository <https://developer.github.com/v3/issues/#list-issues-for-a-repository>`_
* `Get a single issue <https://developer.github.com/v3/issues/#get-a-single-issue>`_
* `List events for an issue <https://developer.github.com/v3/issues/events/#list-events-for-an-issue>`_

Datasets are distributed in ``CSV`` format in the same repository with the rest of the codebase as Git-LFS objects
under `/datasets <https://github.com/mozilla/webcompat-ml/tree/master/datasets>`_.

Available datasets
==================

All events/issues
-----------------

.. seealso::

   - `datasets/all-issues-events.csv <https://github.com/mozilla/webcompat-ml/blob/master/datasets/all-issues-events.csv>`_

This dataset includes all the issue-related historic data available in GitHub. It combines all the issue data available from
the API combined with all the events from each issue. This allows us to go through the lifecycle of each issue and extract features.

Needs diagnosis
----------------

.. seealso::

   - `datasets/needsdiagnosis-balanced-original-titles.csv <https://github.com/mozilla/webcompat-ml/blob/master/datasets/needsdiagnosis-balanced-original-titles.csv>`_
   - `datasets/needsdiagnosis-full-original-titles.csv <https://github.com/mozilla/webcompat-ml/blob/master/datasets/needsdiagnosis-full-original-titles.csv>`_

This dataset is used to train the ``needsdiagnosis`` model. Based on ``All events/issues`` we select all the ``closed`` issues and we extract the ``needsdiagnosis`` feature
based on their events. An issue marked as ``needsdiagnosis`` is an issue that through its lifecycle (issue events) reached the ``needsdiagnosis`` milestone.

Because of the nature of the webcompat issues, the data is unbalanced and have much more data points for ``needsdiagnosis = False``. Trying to factor this in
our model we tried 2 different approaches. The one was to use all the data we have and the other was to balance the entry points so he wave the same number of
``needsdiagnosis = True`` and ``needsdiagnosis = False`` entries.

While going through the data, we noticed an inflation in our metrics which looked suspicious. It turned out that some of the titles get changed as part of the
triaging process which hinted that ``needsdiagnosis`` target. In order to fix that we went through the events and extracted the original titles.

The metrics for the ML model gave more balanced results for the balanced dataset but since we are trying to tackle the problem of having too much noise in our input
we currently use ``datasets/needsdiagnosis-full-original-titles.csv``.
