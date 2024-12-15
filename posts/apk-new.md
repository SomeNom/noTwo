[category]: <> (About)
[date]: <> (2024/12/13)
[title]: <> (Мои приложения Test)

 <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f5f5f5;
      color: #333;
      margin: 0;
      padding: 16px;
      max-width: 800px;
      margin: 0 auto;
    }

    .controls-container {
      margin-bottom: 16px;
    }

    .statistics-grid {
      background-color: #fff;
      border: 1px solid #ccc;
      padding: 8px;
      border-radius: 8px;
      display: flex;
      gap: 4px;
      flex-direction: column;
      margin-bottom: 8px;
    }

    .statistics-grid-columns {
      display: grid;
      grid-template-columns: 1fr 1fr;
      column-gap: 16px;
      row-gap: 4px;
      align-items: center;
    }

    .stat-item {
      display: flex;
      gap: 4px;
    }

    .stat-item b {
      font-weight: 500;
      min-width: 0;
    }

    .stat-item p {
      margin: 0;
      min-width: 0;
      color: #666;
      text-align: right;
      flex: 1;
    }

    .controls {
      position: relative;
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 8px;
      gap: 8px;
    }

    .controls input {
      flex-grow: 1;
      padding: 8px 24px 8px 8px;
      position: relative;
      border: 1px solid #ccc;
      border-radius: 8px;
    }

    .clear-button {
      display: none;
      position: absolute;
      justify-content: center;
      align-items: center;
      right: 0;
      top: 0;
      height: 100%;
      cursor: pointer;
      aspect-ratio: 1 / 1;
    }

    .controls button {
      padding: 8px;
      flex: 1;
      border-radius: 8px;
      border: none;
      background-color: #ccc;

      &:hover {
        background-color: #aaa;
      }

      &:active {
        background-color: #888;
      }
    }

    .app-list {
      width: 100%;
      border-collapse: collapse;
    }

    .app-name {
      font-size: 16px;
    }

    .app-item {
      display: flex;
      align-items: flex-start;
      padding: 8px;
      background-color: #fff;
      border: 1px solid #ccc;
      margin-bottom: 8px;
      border-radius: 8px;
    }

    .app-item img {
      width: 48px;
      height: 48px;
      margin-right: 8px;
    }

    .app-details {
      flex: 1;
      min-width: 0;
      line-break: break-all;
      word-wrap: break-word;
    }

    .placeholder {
      text-align: center;
      padding: 16px;
      font-size: 18px;
      color: #666;
    }

    .filter-modal,
    .sort-modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.5);
      justify-content: center;
      align-items: center;
    }

    .modal-content {
      background: #fff;
      padding: 16px;
      border-radius: 5px;
      width: 80%;
      max-width: 400px;
    }

    .modal-content h3 {
      margin-top: 0;
    }

    .modal-content label {
      display: block;
      margin-bottom: 8px;
    }
  </style>
</head>

<body>
 
  <div class="controls-container">
    <div class="controls">
      <input type="text" id="search-input" placeholder="Search by app name">
      <span class="clear-button" onclick="clearSearch()">✖</span>
    </div>
    <div class="controls">
      <button onclick="toggleSortModal()">Sort Options</button>
      <button onclick="toggleFilterModal()">Filter Options</button>
    </div>
  </div>
  <div class="app-list" id="app-list">
    <div class="app-item"
data-app-name="eSewa"
data-package-name="com.f1soft.esewa"
data-is-system-app="false"
data-is-enabled="true"
data-installer="Google Play Store"
data-default-order="0">
    <img src="data:image/png;base64, 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" alt="eSewa">
    <div class="app-details">
        <strong class="app-name">eSewa</strong><br>
        Платежка. Можно через биржу p2p завести на нее крипту. Можно покупать билеты на автобусы и многое другое. В теории - даже оплачивать визу на границе в Department of Immigration (но у меня не получилось, может в следующий раз...)<br>
        <strong>Links:</strong>
        <a target="_blank" rel="noopener noreferrer" href="https://play.google.com/store/apps/details?id=com.f1soft.esewa">Play Market</a>
    </div>
</div>
  <!-- Sort Modal -->
  <div class="sort-modal" id="sort-modal">
    <div class="modal-content">
      <h3>Sorting</h3>
      <label>
        <input type="radio" name="sort" value="default" onclick="sortBy('default')" checked>
        By default
      </label>
      <label>
        <input type="radio" name="sort" value="installTime" onclick="sortBy('installTime')">
        By install time
      </label>
      <label>
        <input type="radio" name="sort" value="updateTime" onclick="sortBy('updateTime')">
        By update time
      </label>
      <label>
        <input type="radio" name="sort" value="appName" onclick="sortBy('appName')">
        By app name
      </label>
      <label>
        <input type="radio" name="sort" value="packageName" onclick="sortBy('packageName')">
        By package name
      </label>
      <label>
        <input type="radio" name="sort" value="installer" onclick="sortBy('installer')">
        By install source name
      </label>
      <br />
      <div>
        <h3>Order</h3>
        <label>
          <input type="radio" name="sortOrder" value="asc" onclick="setSortOrder('asc')" checked>
          Ascending
        </label>
        <label>
          <input type="radio" name="sortOrder" value="desc" onclick="setSortOrder('desc')">
          Descending
        </label>
      </div>
      <button onclick="toggleSortModal()">Close</button>
    </div>
  </div>

  <!-- Filter Modal -->
  <div class="filter-modal" id="filter-modal">
    <div class="modal-content">
      <h3>Apps Filtering</h3>
      <label>
        <input type="checkbox" id="filter-user-apps" checked> Include user apps
      </label>
      <label>
        <input type="checkbox" id="filter-system-apps" checked> Include system apps
      </label>
      <label>
        <input type="checkbox" id="filter-enabled-apps" checked> Include enabled apps
      </label>
      <label>
        <input type="checkbox" id="filter-disabled-apps" checked> Include disabled apps
      </label>
      <label style="display: none;">
        <input type="checkbox" id="filter-installed-apps" checked> Include installed apps
      </label>
      <label>
    <input type="checkbox" id="filter-installer-google-play-store" checked> Include installed from Google Play Store
</label><label>
    <input type="checkbox" id="filter-installer-package-installer" checked> Include installed from Package installer
</label><label>
    <input type="checkbox" id="filter-installer-n/a" checked> Include installed from N/A
</label><label>
    <input type="checkbox" id="filter-installer-f-droid" checked> Include installed from F-Droid
</label><label>
    <input type="checkbox" id="filter-installer-ffupdater" checked> Include installed from FFUpdater
</label>
      <button onclick="applyFilters()">Apply Filters</button>
      <button onclick="toggleFilterModal()">Close</button>
    </div>
  </div>

  <script>
    const appList = document.getElementById('app-list');
    const installerFiltersData = {"filter-installer-google-play-store":"Google Play Store","filter-installer-package-installer":"Package installer","filter-installer-n/a":"N/A","filter-installer-f-droid":"F-Droid","filter-installer-ffupdater":"FFUpdater",};
    const noItemsPlaceholder = document.getElementById('no-items-placeholder');
    const appItems = [...appList.getElementsByClassName('app-item')];
    let currentSortOrder = 'asc';
    let currentSortCriteria = 'default';
    let installedApps = [];

    function sortBy(criteria) {
      currentSortCriteria = criteria;
      let compareFunction;

      switch (criteria) {
        case 'default':
          compareFunction = (a, b) => a.dataset.defaultOrder - b.dataset.defaultOrder;
          break;
        case 'installTime':
          compareFunction = (a, b) => new Date(Number(a.dataset.installTime)) - new Date(Number(b.dataset.installTime));
          break;
        case 'updateTime':
          compareFunction = (a, b) => new Date(Number(a.dataset.updateTime)) - new Date(Number(b.dataset.updateTime));
          break;
        case 'appName':
          compareFunction = (a, b) => a.dataset.appName.localeCompare(b.dataset.appName);
          break;
        case 'packageName':
          compareFunction = (a, b) => a.dataset.packageName.localeCompare(b.dataset.packageName);
          break;
        case 'installer':
          compareFunction = (a, b) => a.dataset.installer.localeCompare(b.dataset.installer);
          break;
      }

      if (currentSortOrder === 'desc') {
        appItems.sort((a, b) => compareFunction(b, a));
      } else {
        appItems.sort(compareFunction);
      }

      updateAppList();
    }

    function setSortOrder(order) {
      currentSortOrder = order;
      sortBy(currentSortCriteria);
    }

    function filterList() {
      const filterValue = document.getElementById('search-input').value.toLowerCase();
      let visibleItemCount = 0;
      appItems.forEach(item => {
        const appName = item.dataset.appName.toLowerCase();
        const packageName = item.dataset.packageName.toLowerCase();
        if (appName.includes(filterValue) || packageName.includes(filterValue)) {
          item.style.display = '';
          visibleItemCount++;
        } else {
          item.style.display = 'none';
        }
      });
      togglePlaceholder(visibleItemCount);
    }

    document.getElementById('search-input').addEventListener('input', function () {
      filterList();
      const clearButton = document.querySelector('.clear-button');
      clearButton.style.display = this.value ? 'flex' : 'none';
    });

    function applyFilters() {
      const includeUserApps = document.getElementById('filter-user-apps').checked;
      const includeSystemApps = document.getElementById('filter-system-apps').checked;
      const includeEnabledApps = document.getElementById('filter-enabled-apps').checked;
      const includeDisabledApps = document.getElementById('filter-disabled-apps').checked;
      const includeInstalledApps = document.getElementById('filter-installed-apps').checked;

      const activeInstallerFilters = Object.keys(installerFiltersData).filter(
        filterId => document.getElementById(filterId)?.checked
      ).map(filterId => installerFiltersData[filterId]);

      let visibleItemCount = 0;
      appItems.forEach(item => {
        const isUserApp = item.dataset.isSystemApp === 'false';
        const isSystemApp = item.dataset.isSystemApp === 'true';
        const isEnabled = item.dataset.isEnabled === 'true';
        const isDisabled = item.dataset.isEnabled === 'false';
        const installer = item.dataset.installer;

        const showUserApp = includeUserApps && isUserApp;
        const showSystemApp = includeSystemApps && isSystemApp;
        const showEnabledApp = includeEnabledApps && isEnabled;
        const showDisabledApp = includeDisabledApps && isDisabled;
        const showInstallerApp = activeInstallerFilters.includes(installer);

        let isVisible =
          (showUserApp || showSystemApp) &&
          (showEnabledApp || showDisabledApp) &&
          showInstallerApp;
        if (isVisible && !includeInstalledApps) {
          if (installedApps.includes(item.dataset.packageName)) {
            isVisible = false;
          }
        }

        if (isVisible) {
          item.style.display = '';
          visibleItemCount++;
        } else {
          item.style.display = 'none';
        }
      });
      togglePlaceholder(visibleItemCount);
      toggleFilterModal();
    }

    function toggleSortModal() {
      const sortModal = document.getElementById('sort-modal');
      sortModal.style.display = sortModal.style.display === 'flex' ? 'none' : 'flex';
    }

    function toggleFilterModal() {
      const filterModal = document.getElementById('filter-modal');
      filterModal.style.display = filterModal.style.display === 'flex' ? 'none' : 'flex';
    }

    function toggleStatistics() {
      const container = document.getElementById('statistics-container');
      const button = document.getElementById('toggle-statistics-button');
      const isHidden = container.style.display === 'none';

      container.style.display = isHidden ? 'grid' : 'none';
      button.textContent = isHidden ? 'Show less' : 'Show more';
    }

    function togglePlaceholder(visibleItemCount) {
      if (visibleItemCount === 0) {
        noItemsPlaceholder.style.display = 'block';
      } else {
        noItemsPlaceholder.style.display = 'none';
      }
    }

    function updateAppList() {
      appList.innerHTML = '';
      appItems.forEach(item => appList.appendChild(item));
      togglePlaceholder(appItems.length);
    }

    function clearSearch() {
      const searchInput = document.getElementById('search-input');
      searchInput.value = '';
      searchInput.dispatchEvent(new Event('input'));
    }

    function setInstalledApps(apps) {
      const filter = document.getElementById('filter-installed-apps');
      filter.parentNode.style.display = '';
      installedApps = apps;

      let installedAppsCount = 0;

      appItems.forEach(item => {
        if (installedApps.includes(item.dataset.packageName)) {
          installedAppsCount++;
        }
      });

      const uninstalledAppsCount = appItems.length - installedAppsCount;

      const installedItem = document.querySelector("#installed-apps-count p");
      const uninstalledItem = document.querySelector("#uninstalled-apps-count p");

      if (installedItem) {
        installedItem.parentNode.style.display = '';
        installedItem.textContent = installedAppsCount;
      }
      if (uninstalledItem) {
        uninstalledItem.parentNode.style.display = '';
        uninstalledItem.textContent = uninstalledAppsCount;
      }
    }
  </script>